### Saving and loading data
When working with any forms of data, the vast majority of the time you'll have to save it, load it, and transfer it to other devices.
However, you cannot directly save complex objects such as a dictionary to a file, as the way they are represented in memory is specific to Python, and saving the code to recreate them and executing it as python code would be dangerous.

To solve these issues, there are multiple conventions of file formats used to store data, including text formats such as `.csv`, `.json`, `.yaml`, as well as binary formats like `.parquet`. These formats let you work with data separately from the code itself, and come with benefits such as interoperability between different tools and languages.

### Converting data to and from Strings
To work with `json` data, we will need to import the `json` module of the standard library.
You can convert lists or dictionaries to strings using the `json.dumps(object)` function, and load back from strings using the `json.loads(string)` function.

When working with entire files, you'll want to use the `json.load(file)` and `json.dump(object, file)` functions instead.

```py
import json
data = [{"name": "kayn"}]
print(data)
data_as_string = json.dumps(data)
print(type(data_as_string), repr(data_as_string), data_as_string[0])
loaded_data = json.loads(data_as_string)
print(type(loaded_data), repr(loaded_data), loaded_data[0])

# Creating a file:
with open("persons.json", 'w') as file:
	json.dump(data, file)

# Reading from a file:
with open("persons.json", 'r') as file:
	data = json.load(file)
print(data)

# Editing a file: First open and read, then edit in memory, then open and write
with open("persons.json", 'r') as file:
	data = json.load(file)

data[0]["age"] = 27
print(data)

with open("persons.json", 'w') as file:
	json.dump(data, file)

```

When working with larger amounts of data, you may want to look into the keyword arguments it supports such as `indent` to format it in a more human-friendly way if you need to look into it to debug yourself:
```py
with open("persons.json", 'w') as file:
	json.dump(data, file, indent=4)
```

### Limitations
JSON can only represent the following types
- integers
- floats
- bools
- strings
- lists of JSON supported types
- dictionaries mapping strings keys to values of JSON supported types
- the `None` special value

And JSON is not meant to be used as a Database.
It has a relatively poor performance and lacks dozens of features you must have in databases such as ACID Transactions and Indexes, so please consider moving to a Database such as [[Extra/Libraries/Databases/SQLite|SQLite]] or PostgreSQL - It is easier than you'd expect and SQLite is already built into Python, requiring no downloads besides the standard library you already have.

### Further Reading
You may want to use third-party libraries such as [[Extra/Libraries/Generic/Pydantic|Pydantic]] if you are working with more complex data models, or use an actual database such as [[Extra/Libraries/Databases/SQLite|SQLite]] instead of working with JSON

JSON means "JavaScript Object Notation", but it is widely used across all programming languages.