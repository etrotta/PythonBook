### Conceptually
In Python, functions are just objects, much like integers, strings, lists, dictionaries and other data types you should be used to working with by the time you're reading this.

This allows for us treat:

### Functions as Variables
Anything that you can do with normal data types, you can also do with functions.

The "def" syntax may make them look special, but you can also define simple functions using a `lambda` expression:

```py
def add_one(value):
	return value + 1

# Is equivalent to
add_one = lambda value: value + 1
```

In other words, there is nothing inherently special about them. They are just a variable, that happens to be callable as a function.
You can also define functions inside of other functions,

```py
def create_adder(amount_to_add):
	def add_amount(value):
		return value + amount_to_add
	return add_amount

# Alternatively
def create_adder(amount_to_add):
	adder_function = lambda value: value + amount_to_add
	return adder_function


add_one = create_adder(1)
result = add_one(5)
assert result == 6
```

You might want to take a moment to take that in and practice a little on your own before reading further.

Taking things a step further, you are also able to receive functions as arguments:

```py
def chain_functions(value, first_function, second_function):
	first_result = first_function(value)
	final_result = second_function(first_result)
	return final_result

add_one = create_adder(1)
add_two = create_adder(2)

result = chain_functions(10, add_one, add_two)
assert result == 13
```

Takings things even a step further, you could have a function both receive a function and return a new function, 'wrapping' around the original function to modify its behavior:

```py
def add_to_result(original_function, value_to_add):
	def wrapper(*args, **kwargs):
		original_result = original_function(*args, **kwargs)
		new_result = original_result + value_to_add
		return new_result
	return wrapper

def add_one(x):
	return x + 1

add_three = add_to_result(add_one, 2)
assert add_three(10) == 13
```

But for now let's step back a little.
All of that could feel anywhere from 'useless extra complexity' to a perfect fit to some problem you might be trying to solve, so let's take a look at some cases in which you may want to use them in practice.

##### Example 1: Calculator

For this example, our goal is to create a program which will accept user inputs to perform a simple operation (addition, multiplication, subtraction, division) with two numbers, also given by the user.
You should already be familiar with the way we can receive numbers as strings and convert them to floats, but we will need of some way to identify which operation to perform based on the operator.

We could use a series of `if` statements, but that can get annoying, so instead we will use a dictionary to create a direct mapping of `operator identifier as a string -> function for the operation`

```py
# Create a function for each operation we'll support
def add(x, y):
	return x + y

def multiply(x, y):
	return x * y

def subtract(x, y):
	return x - y

def divide(x, y):
	return x // y

# Create a dictionary of string -> function,
# in order to determine which operation to perform based on a given user input
operations = {  
	"+": add,
	"*": multiply,
	"-": subtract,
	"/": divide,
}

def main():
	# Ask for user input, the same way you would in any other script
	a = float(input("Enter the first number: "))
	b = float(input("Enter the second number: "))
	op = input("Enter the operation (+, -, *, /): ")
	# Retrieve the function associated with that operation, just like you would retrieve a string from a dictionary
	function = operations[op]
	result = function(a, b)
	print(f"The result of {a} {op} {b} is: {result}")

main()
```

##### Example 2: Command Decorators

Building upon the same logic as the previous function, we'll now explore how some popular libraries for web servers, bots, chatbots and command line programs let you define commands as functions, and show how they can use the function's metadata to make both documenting the code more convenient for you and more useful for your users.

```py
import inspect

"""Note: The `inspect` module and properties such as `__name__`, `__doc__` are not explicitly covered anywhere in the Book.
You should look up the official documentation in python.org if you want to see the details about them."""

# Helper functions for dealing with the functions metadata
def parse_annotations(func):
	annotations = inspect.get_annotations(func)
	result = []
	for name, cls in annotations.items():
		if name == 'return':
			continue
		result.append({"name": name, "converter": cls})
	return result

def parse_metadata(func):
	parameters = parse_annotations(func)
	name, description = func.__name__.strip('_'), func.__doc__
	return {
		"name": name,
		"description": description,
		"parameters": parameters,
	}

# Function responsible for registering the commands
commands = {}
def register_command(func):
	metadata = parse_metadata(func)
	commands[metadata["name"]] = {"function": func, "meta": metadata}
	return func

# Utility function to format the data
def help_():
	"Print available commands"
	print("Available commands:")
	for command in commands.values():
		meta = command["meta"]
		print(f"> {meta['name']}: {meta['description']}")
		if meta["parameters"]:
			args = [
				f"{arg['name']} ({arg['converter'].__name__})"
				for arg in meta["parameters"]
			]
			print(f"* Arguments: {', '.join(args)}")
		else:
			print("* No arguments")


# Define the actual commands
def congratulate(name: str, age: int) -> str:
	"Wish someone a happy birthday!"
	return f"Happy {age}th birthday {name}!"

def calculate(first_number: float, operation: str, second_number: float) -> str:
	"Perform basic arithmetic operations"
	# Requires much of the `Example 1`'s code in the same file
	function = operations[operation]
	result = function(first_number, second_number)
	return f"The result of {first_number} {operation} {second_number} is: {result}"

# use '_' suffix to prevent conflicting with built-in exit() function
# (this is the reason why the parse_metadata function has .strip('_'))
def exit_():
	"Exit the program"
	exit()

register_command(help_)
register_command(congratulate)
register_command(calculate)
register_command(exit_)

def main(user_command):
	command_name, *args = user_command.split()
	registered = commands[command_name]
	# Convert each argument based on the corresponding parameter's type hint
	# (otherwise it would be just strings)
	converted_args = [
		param["converter"](arg) 
		for arg, param in zip(args, registered["meta"]["parameters"])
	]
	result = registered["function"](*converted_args)
	return result

help_()
while True:
	user_command = input("\nEnter a command with its arguments:\n> ")
	try:
		result = main(user_command)
		print(f"% {result}\n")
	except Exception as err:
		import traceback
		traceback.print_exc()
		print(f"Got an error trying to run the command")

```

Some example inputs to try should you run the program:
```
congratulate Bird 10

calculate 10 + 10

calculate 20 - 50

help

exit
```

### Decorators

Strictly speaking, decorators are just an alternative syntax of what we have already done above. Such "alternative syntax" things are also called "syntax sugar". In practice:

```py
@decorator
def function():
	...

# Is just the same as:
def function():
	...

function = decorator(function)
```

However, they do allow for you to define things in a more readable way at times. For example, you could have used `register_command` as a decorator on the Example 2 to eliminate the need to call it separately:
```py
@register_command
def congratulate(name: str, age: int) -> str:
	"Wish someone a happy birthday!"
	return f"Happy {age}th birthday {name}!"

@register_command
def calculate(first_number: float, operation: str, second_number: float) -> str:
	"Perform basic arithmetic operations"
	# Requires much of the `Example 1`'s code in the same file
	function = operations[op]
	result = function(a, b)
	return f"The result of {a} {op} {b} is: {result}"
```

It gets a bit weird if you want for the decorator to receive arguments, but not far too bad either.

Showing an example of how you might create a function similar to `register_command`, but supporting decorator arguments: 
```py
def register_command(name: str, description: str):
	def decorator(func):
		metadata = parse_metadata(func)
		# In practice you may want to create a function like
		# metadata = combine_metadata(metadata, name=name, description=description)
		metadata["description"] = description
		commands[name] = {"function": func, "description": description, "meta": metadata}
		return func
	return decorator

@register_command("congratulate", "Wish someone a happy birthday!")
def wish_happy_birthday(name: str, age: int):
	return f"Happy {age}th birthday, {name}!"

@register_command("exit", ""Exit the program"")
def exit_program():
	exit()
```

If you want to explore the example further, as well as add your own spin to it, here are some ideas for you to challenge yourself:
- try creating the suggested `combine_metadata` function, using optional parameters to support getting the name automatically from `__name__` or overwriting it (and same for description)
- add more forms of "converters", for example a command could let you refer to users using `@user` and fetch more data about them from a dictionary or a [[Extra/Python Operations/Working with JSON|JSON]] file
- support Variadic arguments or Keyword arguments
- just create more commands

