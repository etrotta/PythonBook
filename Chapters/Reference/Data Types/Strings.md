# Conceptually
Strings can represent any text, such as this book's contents, a social network post, data read from text files, input from users, or "hello world".

In Python, Strings are collections of characters, but at the same time, individual characters themselves are also treated as strings.

Strings are created by entering any text within quotes, `"..."` or `'...'`. You can also use triple quotes for multiline strings or including quotes inside of strings, `"""Hello World"""`, `'''Who's "World"?'''`

Unlike most other forms of collections, strings are [[Extra/Abstract Concepts/Mutability|Immutable]]. This means that you cannot modify an existing string, but rather you must create a new string whenever you want to do operations on them - for example, if you want to modify a character, you have to call `replace()` which will return a new string or slice it and add the parts back together.

Numbers also share this property, but it is less noticeable when working with them.

# Operations and functions

^38dca1

Do not worry about memorizing all operations, always feel free to come back to the reference whenever you need.

### Common use cases
You may need to do operations on Strings to remove whitespace, join multiple strings together, fix problems such as mislabeled data, or format strings for humans to see the program's output or help yourself debug it.

You can prepend `f` or `r` before string literals to use f-strings or raw strings, with f-strings being used for formatting, and raw strings being used to prevent `\` from being interpreted as part of [escape codes](https://realpython.com/python-encodings-guide/#python-string-literals-ways-to-skin-a-cat) like `'\n'` (newline), `'\U0001f408'` (Unicode) or `'\N{CAT}'` (Unicode by name)

```
who = "world"  # normal string
print(f"Hello, {who}")  # f-string
filename = r"""C:\Users\User\test.txt"""  # raw string
```

### String Formatting

^c697af

Formatting strings is one of the most common operations you have to do with them, for example adding extra information about the values being printed, visually aligning them in tables, or setting a fixed number of decimal places. 

You can use f-strings - strings prefixed with `f` as in `f"{variable}"` - to perform String Interpolation, injecting variables or expressions directly into the string: `f"X times two is equal to: {x * 2}"`. Alternatively, you can create first create a template string then call `format()`, and you may use Formatting Specifiers to format it in both cases.

> [!tip]- Extra - Types that support fancier formatting
> Some types such as [[Extra/Libraries/Standard Library/Modules/Datetime|Datetime]] support fancier formatting specifiers, for example `f"Today is {today:%A}, day {today:%d of %B of %Y}"`.

%% NOTE: MENTION THE \_\_FORMAT\_\_ MAGIC METHOD ONCE I COVER CLASSES %%

> [!warning]- Warning - SQL Injection risks
> If you are using a Relational Database such as PostgreSQL, SQLite or MySQL, you must be careful not to inject user provided strings directly into your database queries. See [[Extra/Libraries/Databases/SQLite#^67c3f4|Databases - SQLite]] for an example of how to inject parameters safely into an SQLite query (it should be a similar process for other databases, read the documentation of the driver you are using to connect to your database)

##### Format Specification Mini-Language

^232a00

You can see the [documentation online](https://docs.python.org/3/library/string.html#formatspec) or use `help('FORMATTING')` inside of a Python interpreter to consult the official documentation, describing everything you can do with it, but here are some particularly common operations you'll want to use:

- Fill and Align: You can specify minimum length, (optionally) a fill character, and (optionally) how to align the string. `[fill_char][< ^ > =][minimum_length]`
- Float relevant decimal places: You can specify the number of digits you want to display

Some examples:
```
a, b, c, x, y, z = 1, 12, 12e10, 0.1, 1.2, 12e-10

print("   a   |   b   |   x   |   y")
print(f" {a:0>5} | {b:0>5} | {x:0>5} | {y:0>5}")
print(f" {a:^5.2f} | {b:^5.2f} | {x:^5.2f} | {y:^5.2f}")
```

### String Operations
- Get a character by index: `string[index]`, with the first character being at `index=0`
- Get a substring by index: `string[start_index:end_index]`
	- Further reading: [[Chapters/Reference/Operations/Indexing and Slicing|Indexing and Slicing]]
- Concatenating: `a + b`, creates a new string by joining them together
- Check if string contains substring: `substring in string`
- Repeating a string multiple times: `string * integer`
- Get the length of a string: `len(string)`
- Old style string formatting: `string % (arg1, arg2)`. Please don't use this - See the **String Formatting** section for the modern way to do string formatting. If using `{}` for the placeholders is impractical for your use case, look into the `string.Template` class from the `string` standard library module.

### String Functions
Remember: All functions that make changes to the string's contents will return a new string, they never modify the variable directly. You have to re-assign to save the result of the operation, as in `foo = foo.upper()`.

- Changing the capitalization:
	- `upper()` - Convert to UPPERCASE
	- `lower()` - Convert to lowercase
	- `casefold()` - Like `lower()`, but includes additional operations relevant for certain languages
	- `title()` - Convert To Title Case
- Modify parts of it
	- `replace()` - Replace a substring by a different substring. 
	- `removesuffix()`, `removeprefix()` - Remove a substring from the end or the start of the string
	- `lstrip()`, `rstrip()`, `strip()` - Removes all characters from the left, right or both sides of the string. If called with no arguments, it removes whitespace
	Unlike `removeprefix`/`removesuffix`, these functions only care about matching the characters, not their order or length, so `"abacbab".strip("ab")` would leave you with only `"c"`
- Test properties about it
	- `isupper()`, `islower()` and alike - Tests if it would be equal to the corresponding transformation
	- `startswith()`, `endswith()` - Tests if it has that prefix or suffix
	- `isalpha()`, `isalnum()` - Tests if it is an alphabetic (letters only) or alphanumeric (letters or integers) string
	- `isdigit()`, `isdecimal()`, `isnumeric()` - You probably want the first, which essentially checks if it's a valid positive integer. The others refer to Unicode properties.
	There is no operation that can check if a string is a valid float. See [[Chapters/Reference/Operations/Exceptions#^b187e0|Handling Exceptions]] examples if you are looking for that.
- Other functions
	- `.index()` and `.find()` - Find the position of a substring. The difference between them is what happens if it is not present, raising an error or returning -1
	- `string.split(separator)` and `list(string)` - Convert this string into a List, containing either parts delimited by the separator or each character as a separate element.

These are only some of the most important functions. See the official Documentation for all available functions.
You can also use `dir(str)`, `help(str)`, or `help(str.method)` inside of the Python interpreter to see more information about their methods.

### See also

Like nearly all types in Python, Strings also support [[Chapters/Reference/Operations/Logical Operations|Logical Operations]]

See [[Chapters/Reference/Operations/Indexing and Slicing|Indexing and Slicing]] for more advanced indexing and slicing operations, which are also usable on strings.

### Further Reading

##### Unicode and Text Encodings
https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/

##### Saving, Loading, Parsing data
A lot of the time your input will come in the form of strings, but you will want to convert it to numbers or other objects such as dictionaries.
We cover basic conversions of strings into numbers as part of [[Chapters/Reference/Operations/Exceptions#^b187e0|Handling Exceptions]], but for more complex data formats, you may want to use [[Extra/Python Operations/Working with JSON|JSON]], possibly with third-party libraries such as [[Extra/Libraries/Generic/Pydantic|Pydantic]]
