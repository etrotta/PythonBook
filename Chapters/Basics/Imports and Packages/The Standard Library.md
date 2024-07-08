### Using code written by others

We have used the `import` statement in a few places before this chapter without explaining it, such as `from math import pi`.

In these cases, we were importing from the Python Standard Library, which contains a lot of modules that are installed alongside Python when you install it.

These modules include a lot of functions you can use, removing the need to write those functions yourself or even allowing for you to do things you otherwise wouldn't be able to in Python.

Some modules I recommend looking into include:
- [[Extra/Libraries/Standard Library/Modules/Math|Math]], with functions like `sqrt`, `sin`, `cos`, `log`
- [[Extra/Libraries/Standard Library/Modules/Random|Random]], with functions like `random`, `randrange`, `shuffle`, `choices`, `sample`
- [[Extra/Libraries/Standard Library/Modules/Datetime|Datetime]], with classes for `datetime`, `timezone` and `timedelta`, that let you work with dates
- [[Extra/Libraries/Standard Library/Modules/Functools|Functools]], with utility functions such as `cache`, `partial`, `reduce`, `wraps`
- [[Extra/Libraries/Standard Library/Modules/Itertools|Itertools]], with utility functions such as `accumulate`, `combinations`, `permutations`, `product`, `repeat`
- [[Extra/Libraries/Standard Library/Modules/Regular Expressions|Regular Expressions]], which provide some more powerful string operations
- [[Extra/Python Operations/Working with JSON|JSON]], used for saving and loading objects in a common text format
- [[Extra/Libraries/Databases/SQLite|SQLite]], that allows for you to interact with databases

And some more that might be useful once you look into Object Oriented Programming and defining your own classes:
- [[Extra/Libraries/Standard Library/Modules/Dataclasses|Dataclasses]], which provide an alternative syntax to define classes
- [[Extra/Libraries/Standard Library/Modules/Collections|Collections]], with abstract base classes for multiple types of collections such as `Sequence` or `Mapping`

### Exercises

I recommend picking 2 or 3 of them to do, do not worry about completing all of them - and even inside of the ones you did pick, feel free to skip some if there are too many.

- [[Chapters/Excercises/Libraries/Random 1|Random 1]]
- [[Chapters/Excercises/Libraries/Math 1|Math 1]]
- [[Chapters/Excercises/Libraries/Regex 1|Regex 1]]
- [[Chapters/Excercises/Libraries/Datetime 1|Datetime 1]]
- [[Chapters/Excercises/Libraries/SQLite 1|SQLite 1]]

### Next Steps

All of the libraries mentioned in this page are included by default when you install Python.
Follow to [[Chapters/Basics/Imports and Packages/Third-Party Packages|Third-Party Packages]] to learn how to install packages made by other users, organizations or companies, and see some of the most popular ones.
