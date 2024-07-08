### Conceptually

Using the `input()` and `print()` functions allows for programs to interact with users, but performing Input/Output that way requires for a human to enter all information and as save the outputs manually.

Writing to files lets us save information for programs to use later - both our own as well as others - without requiring for a human to manage the data manually, and the same goes for reading from files.

### Working with files

You have to create a connection to a file by using the `open()` function, specifying if you want to read from or write to the file, then close the connection when you're done with it.

```py
# 'w' for writing
file = open("test.txt", 'w')
file.write("Hello World!")
file.close()

# 'r' for reading
file = open("test.txt", 'r')
print(file.read())
file.close()
```
You can also use `'wb'` and `'rb'` for working with bytes, but we won't really cover that in this book.

However, if anything goes wrong when working with files in that way, Python may not close the connection properly, which could cause all sort of issues.
As such, you should prefer using [[Chapters/Basics/Input and Output/Context Managers|Context Managers]] via the `with` statement, which will automatically close the connection and clean up for you even if any errors happen:
```py
with open("test.txt", 'w') as file:
	file.write("Hello world!")

with open("test.txt", 'r') as file:
	data = file.read()

print(data)
```

%% That usually does not matters *that* much for files, but it does matters a lot when working with other types of connections such as databases. As general rule, you should strongly prefer using `with` statements when available. %%

### File paths

When you open a file like `open('file.txt')`, Python will assume that you are referring to a path relative to your **current working directory**.

When running things from your terminal, you should always know what is your current working directory, but it can be less obvious in other cases such as running files by double-clicking them or having your IDE run your code for you.

You may want to print it if you ever get lost:
```py
from pathlib import Path

print(Path.cwd())

input("Press enter to close")  # So that it does not closes automatically when running by double-clicking
```

You can also just use absolute file paths instead, in which case your current working directory would not matter.

### Exercises

Try updating some of your previous exercises to read their input from files instead of using fixed values, and write to files instead of using `print()`

[[Chapters/Excercises/Files 1|Files 1]]

### See Also

I strongly recommend seeing [[Chapters/Basics/Input and Output/File Encodings|File Encodings]] to get an idea of how data is stored inside of files, as well as seeing how to store non-textual data such as numbers, lists and other collections.

Check the [[Chapters/Reference/Operations/File Streams|File Streams Reference page]] for a list of some more common operations you can do with files

You may also want to look into the following standard library modules:
- See [[Unorganized/MISSING|Pathlib]] for a more pythonic way of working with file paths rather than manipulating strings, great for operations such as getting to paths relative to the current file.
- See [[Extra/Python Operations/Working with JSON|Working with JSON]] or Databases such as [[Extra/Libraries/Databases/SQLite|SQLite]] to see how to save structured data in common formats
