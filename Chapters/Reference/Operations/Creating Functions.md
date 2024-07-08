### Conceptually
Functions let you define operations once and use them multiple times, in multiple different contexts, while providing a way of abstracting way the set of instructions into one single named operation.

This lets you think of more complicated algorithms not only as a series of individual basic operations, but rather as a chain of more abstract operations, designing them around existing functions implemented by you or made available by third-party packages.

### Basic Functions

To define a function, you have to use a `def` statement followed by the function's name and the parameters specifying which arguments it will receive.

> [!tip]+ Parameters vs Arguments
> Both refer to the same concept: Variables you can pass into functions to tell them which values to operate on.
> 
> That said, we refer to the variables declared on the function's definition as the **parameters** it receives, and the actual values given to the function when calling it as the **arguments** you are passing to the function.

```py
# Define a function called `add`, with the parameters `x` and `y`
def add(x, y):
	result = x + y
	print(result)

add(10, 20)  # prints 30
```

Functions are also able to **return** values to whatever called them, allowing for you to further use their results inside of your program.

```py
def add(x, y):
	return x + y

result = add(10, 20)
print(result)
second_result = add(result, 30)
third_result = add(result, 40)
print(third_result)

"""Expected output:
print(result) -> prints 30
second_result is not printed, so it is not displayed
print(third_result) -> prints 100
"""
```

Usually it's preferable to return values instead of printing them directly inside of functions, as that allows for you to use them in many other ways such as calling another function in succession.

Functions are also able to call other functions, as well as do just about everything you can do outside of functions we'll learn more about later.
```py
def add(x, y):
	return x + y

def product(x, y):
	return x * y

def linear(x, a, b):
	prod = product(x, a)
	result = add(prod, b)
	# You could also write it as
	# result = add(product(x, a), b)
	return result

print(linear(10, 20, 30))
```

> [!important] Indentation
> In Python, many statements including functions use indentation (spaces or tabs at the start of a line) to determine what is "inside" of the statement, and when does the statement ends.
> 
> The space before lines within a function is not only a stylistic choice, but rather it's what Python uses to determine what is inside of the function.

### Documenting your functions

Python also offers some ways to document your function, that are directly integrated with your IDE.

You can write a string on the first line after a function to give it a description (also called a "docstring"), and you can specify the types of each parameter the function defines, as well as its return type.
- For parameters, that is done by specifying the type after `:` as in `value: int` or `name: str` 
- For the return type it's done by adding a `->` between the parameters `(...)` and the `:`


Neither of these affect the program's execution - they are essentially standardized forms of adding comments to your code.

```py
def linear(x: int, a: int, b: int) -> int:
	"Calculates the result of a linear equation y=ax + b"
	return a*x + b
```

Note: The `->` might look like $\to$ in some fonts, but that is a visual effect combining two characters called a ligature. In practice, it is two characters, `-` followed by `>`.

### Further Reading

You'll learn about [[Chapters/Reference/Abstract Concepts/Recursion|Recursive Functions]] after learning about control flow statements and normal loops as you follow the Read Order.

Once you complete the Basic Chapters, you may want to dive deeper into functions and everything you can do with them, such as:
- Creating more [[Extra/Abstract Concepts/Advanced Functions|Advanced Functions]], showing different ways you can configure function parameters and arguments.
- Treating [[Extra/Abstract Concepts/Functions as Variables|Functions as Variables]] and the implications of that: Functions are just another type of variables as far as Python is concerned, so everything you can do with variables, you can do with functions. We will look into what that entails in this Extra Chapter.
