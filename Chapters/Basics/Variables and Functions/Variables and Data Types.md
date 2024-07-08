# Variables
Solving problems is all about breaking them down into smaller steps, and Variables are the smallest steps in your program.
If you wanted to solve an equation `x = (16 + 14) * 13`, you may first break it down into `y = (16 + 14)` then solve `x = y * 13`. Those are Variables, and this is precisely how you would define them in Python - `variable_name = expression`
```py
y = 16 + 14
x = y * 13
print(x)
```
For this case, you could write it down into a single step `print((16 + 14) * 13)`, but breaking down into atomic steps make it easier to visualize each step of the problem and find which step is wrong when tracking down bugs.

# Data Types Overview
So far we have worked with numbers and strings, and used Python as a calculator to do simple math operations, but those are just some of the types of data it supports.

We will look over some of the following built-in types soon, to give an idea of what's coming over the next chapter:

- [[Chapters/Reference/Data Types/Numeric Data Types|Numbers]]
	- `int` - Integers
	- `bool` - Booleans
	- `float` - Floating point precision numbers
	- `complex` - Complex numbers
- [[Chapters/Basics/Variables and Functions/Types of Collections|Collections]]
	- `str` - [[Chapters/Reference/Data Types/Strings|Text Strings]]
	- `list` - [[Chapters/Reference/Data Types/Lists|Lists]]
	- `dict` - [[Chapters/Reference/Data Types/Dictionaries|Dictionaries]]
	- `tuple` - [[Chapters/Reference/Data Types/Tuples|Tuples]]
	- `set` - [[Chapters/Reference/Data Types/Sets|Sets]]
	- Extra (optional) - other [[Extra/Libraries/Standard Library/Modules/Collections|Standard Library Collections]]
- Other
	- `None` - A somewhat [[Chapters/Reference/Data Types/Special Values#^3bff32|special value]]
	- Functions - [[Chapters/Basics/Variables and Functions/Functions|Functions]]

> [!info]+ Other types we are not using
> In practice, you'll oftentimes want to use other types defined in the Standard Library, in third-party packages, or create your own Classes, but we will only cover any of that much later in this book.

For this page's exercises, we will start by only using [[Chapters/Reference/Data Types/Numeric Data Types|Numeric Data Types]] and [[Chapters/Reference/Data Types/Strings|Strings]], so take a quick look at their operations and do not worry about the others.
Do not worry about memorizing all details, just try to understand what sort of things you can use them for, and go back to the reference when you actually need of an specific operation.
We will ignore collections besides `str` at first, but you can read [[Chapters/Basics/Variables and Functions/Types of Collections|Types of Collections]] ahead of schedule if you want to take a look at them.

# Notes about Operations

Expressions such as `a + b`, `a * b`, `a == b` or `a in b` are resolved based on the [Operator precedence order](https://docs.python.org/3/reference/expressions.html#operator-precedence), but I strongly recommend using `()` to explicitly state the order in which you want for things to resolve, even if it is the same as the precedence order - that greatly helps with visual clarity and may help reduce bugs.
For example, instead of `2 + 3 * 4` write `2 + (3 * 4)`

# Next Steps

You should practice writing code a bit to get used to it, then proceed to learn about Functions

- Exercises:
	- [[Chapters/Excercises/String Operations 1|String Operations 1]]
	- [[Chapters/Excercises/Numeric Operations 1|Numeric Operations 1]]
- Next chapter: [[Chapters/Basics/Variables and Functions/Functions|Functions]]
