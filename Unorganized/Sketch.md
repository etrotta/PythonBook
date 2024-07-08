
# 0 Installing Python
Two paths:
- python.org CPython + IDLE
- python.org CPython + VSCode + Python extension + Virtual Environment

# 1 Hello World
Your first Python program and instructions on using Python as a calculator
First create, save and run the file from inside the IDE
After that run it from the terminal, after that explain how to use the interpreter directly.

# 2 Variables and Functions
## Data Types
TODO Explain about int, float, str, bool
Do not mention input() yet
### Formatting Strings
f-strings syntax, link to read about formatting specifiers

## Variables
It can be repetitive and confusing to type the same things over and over, so it would be nice if we could explain to the computer that "whenever I am talking about this `<variable>`, I'm referring this `<value>`".
To define a variable, you have to use the `=` operator to assign the `<value>` to the `<variable name>` you want to use for it, as `name = value`. For example:
```py
# operations that would greatly benefit from variables
```

## Functions
And taking it even further, we can also define operations: "whenever I am talking about this function, I'm referring this operation".
To create functions, you have to use the `def` keyword, followed by the function name, followed by its parameters. For example:
```py
def add_one(x):
    x_plus_one = x + 1
    print(x_plus_one)

add_one(10)
```

However, you might notice there is something missing from that example - What if you wanted to do something else with `x_plus_one` instead of just printing it?
You may see some places use global variables, but these are considered bad practice and I recommend avoiding them altogether. Instead, functions can and should return values {mention Yield Appendix}, like the following:
```py
def add_one(x):
    return x + 1

plus_one = add_one(10)
plus_two = add_one(plus_one)
print(plus_two)
```

### Print versus Return
A common question you might ask is, what is the difference between printing and returning?

- Printing: Displays a given value to the user
- Returning: The function returns a value to the place that called it, or in other words, it reports back the result of what you asked it to do

You do not have to print the return value - it could be used internally for other calculations.
In fact, not all programs have to print something - for example, you could write to a file or save the results to a database instead of printing.


# 3 Lists, Dictionaries {Tuples, Set: Appendix or later}
Now that we have ways to work with individual values, you might be asking yourself - but what if I want to work with multiple of the same thing?
For that sort of problems, we have some types of data that act as collections of others.
For example, you may have a list of strings with the names of your friends
```py
friends = [
    "kuro",
    "shiro",
]
# add a new friend
friends.append("luna")
# remove an existing friend
friends.remove("shiro")
# get a friend by its position
print(friends[0])
```
or a dictionary that keeps tracks of their contact information
```py
friends = {
    "kuro": "+42 0000-0000",
    "shiro": "+42 9999-9999",
}
# add a new friend's contact info
friends["luna"] = '+42 1111-1111'
# remove an existing friend's contact info
del friends["shiro"]
# get the contact information from its name
print(friends["kuro"])
```
Now, that might look like a lot of new syntax all at once, but stay calm and remember to refer to the Cheat Sheet as you write your code.

Those are only some of the data types - there many are other commonly used ones such as ranges, tuples, and sets, but you do not have to worry about them for now.

# 4 Loops {Recursion: Appendix?, While: Later?}
TODO Mention terminology iteration, iterating, iterator, etc
enumerate()

Now that you have a way of organizing your lists and dictionaries, you have to actually make use of them, and surely using `[0]`, `[1]`, `[2]`... is not a good way of doing it.
When you want to perform an operation for each element in a list or a dictionary, you have to use Loops such as `for element in collection:`
```py
for friend in friends:
    print("Hello", friend)
```
That works as if you called a function for each element within the list, with it running the indented code inside of the block one time for each element in the collection.
There are no restrictions to what you can do inside of the loop, even include other loops:
```py
print('i * 1  |  2  |  3  |  4  |  5 ')
for i in [1, 2, 3, 4, 5]:
    print(f'{i} | ', end='')
    for j in [1, 2, 3, 4, 5]:
        print(f'{i * j :>3} | ', end=' ')
    print()  # for a new line
```


# 5 Branching {Match: Appendix}
## If, Else
Everything we have written so far does one thing, but what if we wanted to do different things based on our variables?
```py
for x in [16, 4, 0, -4, -16]:
    if x >= 0:
        root = x ** (1/2)
        print(f"Root of {x}: {root}")
    else:
        print(f"{x} has no real root")
```

## Elif
Sometimes, you need to check for more than two conditions. In these cases, you may want to use `elif`, an abbreviation of "else if". For example
```py
for a, b, c in [[1, -5, 6], [1, -4, 4], [1, 0, 12]]:
    delta = b ** 2 - 4*a*c
    if delta > 0:
        root_1 = (-(delta ** 0.5) - b) / (2 * a)
        root_2 = ((delta ** 0.5) - b) / (2 * a)
        print(f"Equation {a}*x**2 + {b}*x + {c} has two roots {root_1} and {root_2}")
    elif delta == 0:
        root = (- b) / (2 * a)
        print(f"Equation {a}*x**2 + {b}*x + {c} has one root {root}")
    else:
        print(f"Equation {a}*x**2 + {b}*x + {c} has no real root")
```
You can also chain multiple `elif`s, with or without an `else` in the end ```py
if x == 0:
    ...
elif x == 1:
    ...
elif x == 2:
    ...
elif x == 3:
    ...
```

Though you might want to try using a dictionary instead if you see yourself doing this too often

## While
`while` loops are another form of Loop we did not mention previously.
Usually, `for` loops are used to iterate over something with known size, such as a list you already have.
In contrast, `while` loops are used to iterate until some arbitrary condition is fulfilled, which may or may not be related to collections.

```py
x = 7
while x > 1:
    print(x)
    if x % 2 == 0:
        x = x // 2
    else:
        x = x * 3 + 1

```
> link to Veritassium's Collatz


# 6 Inputs and Outputs {Appendix: requests}

So far we have been writing values directly into our code, and using print() to see the results. However, a lot of the time we will want to run the same code for different data, that may come from a multitude of different sources.

## Getting data into your program

### Input function
The easiest way to get user input is using the input() function, which will prompt you for a value.
```py
name = input("Enter your name: ")
print(f"Hello, {name}!")
```
Do note that it always returns the input a string, so if you want to accept numbers or other types, you'll need to convert it using operations such as `int()` or `float()`.
``py
x = input('X: ')
y = input('Y: ')
print(x + y)

x = float(input('X: '))
y = float(input('Y: '))
print(x + y)
```

### Reading files
In order to interact with files, you must use the `open` function, preferably alongside the `with` context manager.
```py
with open("file.txt", 'r') as file:
    for line in file:
        print(line)
```
If you want to read binary data, you can use `'rb'` instead of `'r'` 

For information about Context managers, see the Apendix, though you can just use it as-is for now.

### Command Line Arguments
In order to read command line arguments (which you can specify when calling through a terminal, for example `py myfile.py arg1 arg2 arg3 --arg_name named_arg`), you must import `sys` or `argparse`.
```py
import sys
print(sys.argv)
```
Imports and the standard library will be covered in more detail in # TODO ADD CHAPTER NUMBER

## Getting data out of your program

### Print function
We have already been using it for a while, but formally introducing it:
The print() function lets you output text to the standard output, which is usually connected to your terminal when you are running things, but you can also redirect it when running from the terminal, for example
```py
# main.py
print("Hello", "World", sep=" ", end="!\n")
```
```sh
py main.py > text.txt
```

### Writing files
Much like reading from them, you must use the `open` function, but using a different mode this time - `w`rite or `a`ppend. Do not try to read and write within the same context manager.
```py
with open('file.txt', 'r') as file:
    lines = file.readlines()

for i, line in enumerate(lines):
    lines[i] = f'> {line} <'

with open('file.txt', 'w') as file:
    for line in lines:
        file.write(line)
```



# 7 Error Handling

# ? Imports

## The Standard Library
### math
### random
### os
### sys
### Other recommendations
pathlib, itertools, functools, argparse, dataclasses
## Third party tools
### requests
### numpy

# ? Testing

## Unit Test

## Pytest

# ? Building your own Project

#! <Not sure if Appendix, link external resource, out of scope or what>
- SQL/SQLite3
- OOP
- Packaging
- Git
- Type Hints










