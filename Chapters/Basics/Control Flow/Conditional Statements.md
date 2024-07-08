### Checking for conditions: Using the `if` statement

So far, all exercises would always do the exact same thing every time you run the program.
In most real applications, you would need to deal with branching paths or different conditions based on function arguments, user input or other variables that may be outside of your control.

`if` statements let you specify certain parts of the code to only be executed if a given condition is true:

```py
def absolute(number: float) -> float:
	if number < 0:
		return -number
	return number
```

```py
first = float(input("Enter the first number: "))
second = float(input("Enter the second number: "))
method = input("Select an operation: ")
if method == "add":
	print(first + second)
if method == "subtract":
	print(first - second)
```

See [[Chapters/Reference/Operations/Common Conditions|Common Conditions]] for some examples of practical use cases for `if` statements

> [!note] User Input
> We'll cover it in more detail in a later chapter, but the easiest way (and comparable to `print()`) to receive input from the user running the program is the `input()` function. It will return whatever the users types as a string once they press `Enter`, and it may optionally include a string to show to the user.

### The `else` statement

`else` statements can be used in conjunction with `if` statements to perform an operation when the `if` statement is not triggered,

```py
number = float(input("Enter a number: "))

if number > 0:
	print(f"The square root of {number} is {number ** 0.5:.3f}")
else:
	print("Negative numbers do not have a real square root")
```

In the first `if` example, you do not need to use an  `else` statement because it'll exit the function as soon as it `return`s.

### Chaining multiple conditions: `elif` statement

If you need to chain multiple conditions, you could do it as 
```py
if x == 0:
	... # A
else:
	if x == 1:
		... # B
	else:
		if x == 2:
			... # C
		else:
			... # Z
```

However, Python offers an `elif` statement that's essentially an '`else if:`'
This chain of `elif` statements work the same as the above chain:

```py
if x == 0:
	... # A
elif x == 1:  # If the `if` was not triggered AND `x == 1`
	... # B
elif x == 2:  # If none of the `if`/`elif`s above were triggered AND x == 2
	... # C
else:  # If neither the `if` nor any of the `elif`s were triggered
	... # Z
```

### About Indentation and Scope

##### Indentation Refresher

As you may have noticed, `if/elif/else` statements all use Indentation the same way functions do.
As a short refresher:
- Anything indented inside of the block will be part of that statement
- As soon as you un-indent, that exits the block
You have to exit the current `if/elif` statement to chain the next `elif/else`, but it has to be matching the level of the statement you want to chain from.

```py
if A:  # A
	if B:  # B
		...
	elif C: # Chaining from B, will be triggered `if A and (not B) and C`
		...
	else D:  # Chain from C, will be triggered `if A and (not B) and (not C)`
		...
else E:  # Chaining from A, will be triggered `if not A`
	...
```

##### Variable Scope

When working with functions, variables defined within the function only exist inside of the function.
However, that is different when working with conditional and looping statements - they do not create a new scope in Python.

```py
if True:
	x = 10
else:
	x = 5
print(x)  # prints 10
```

When using `if` statements to define variables, remember to define a value in _all_ possible cases by using `elif`/`else` statements, or raise an error / exit the program when you reach a state that shouldn't be possible.

### Exercises

- Exercise: [[Chapters/Excercises/Dictionary Operations 2|Dictionary Operations 2]]
- (Optional) Challenge: [[Chapters/Excercises/User Input 1|User Input 1]]

### See Also

We'll see more details about handling user input in [[Chapters/Basics/Input and Output/Input and Print|Input and Print]], which is right after [[Chapters/Basics/Control Flow/Looping over data|Looping over data]] in the Read Order, but you can see it now if you wish - just remember to come back to Loops.

For some kinds of conditions that may be complex to express with `if` statements, you can use `match/case` statements [[Chapters/Reference/Operations/Pattern Matching|Pattern Matching]]

