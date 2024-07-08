
### How computers store information

Everything in computers are sequences of bytes, including objects in python and all contents of all files.

When working with objects in Python, it will keep track of how to represent each of them, be it as strings, numbers, lists, dates or other types of objects - however, when writing data to files, you'll need to store it in a way that is not dependent on Python's internal representation, which means converting them to standardized formats.

A common example of different formats you may have seen are images, with formats like `.png` or `.jpeg`, but there exist a lot of different formats for all sorts of data, even strings.

### Working with text files

When you open files in `r` or `w` mode, Python will automatically convert data read from bytes into strings when reading and vice-versa when writing.

However, even strings do have to be encoded in some way .
%% TODO LINK EXTERNAL `TEXT ENCODING` RESOURCE %%
Common characters like English alphabet letters and Arabic numerals are typically encoded the same across most text encodings, but when working with anything outside of this subset you should preferably specify which string encoding to use, with a good default being `UTF-8`

For example:
```py
with open("file.txt", 'w', encoding="UTF-8") as file:
	file.write('こにちは')  # Hiragana
	file.write('猫')  # Kanji
	file.write('\N{CAT}')  # Escape sequence for the cat emoji

```

Also keep in mind that whichever program opens the file later will have to use the same encoding that was used to create the file.

If you don't specify which encoding to use, [the default might vary based on your Operating System and Python version](https://peps.python.org/pep-0686/)

### Working with other formats

When opening a file in binary mode, it'll work directly with the bytes without converting anything

```py
with open('file.bin', 'wb') as file:
	file.write(bytes([10, 20, 0x10, 42, 0xff]))

with open('file.bin', 'rb') as file:
	a, b, c, x, y = file.read()

print(a, b, c)
print(x, y)
```

But overall you should avoid manipulating bytes directly - look into formats such as [[Extra/Python Operations/Working with JSON|JSON]] or CSV, or actual databases such as [[Extra/Libraries/Databases/SQLite|SQLite]] if you want to store complex data types, or look for third-party libraries that handle the conversion for you.

```py
import json

data = [10, 20, 30, 42, 255, 999]

with open('file.json', 'w') as file:
	json.dump(data, file)

with open('file.json', 'r') as file:
	a, b, c, x, y, z = json.load(file)

print(a, b, c)
print(x, y, z)
```

%%
I'm intentionally NOT mentioning `pickle` / `shelve` standard library modules.
These are major security vulnerabilities and not interoperable with other programs. I strongly recommend avoiding them.
%%

### See Also

[[Chapters/Reference/Operations/File Streams|File Streams]]
%% maybe something about text encodings %%