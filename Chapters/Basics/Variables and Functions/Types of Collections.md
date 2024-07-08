### Conceptually

Collections are used whenever you want to store multiple similar or related values in the same place, such as a series of numbers, information about a given person, or a set of valid values.

```py
numbers = [1, 2, 3, 4, 5]
person_data = {"name": "kayn", "age": 25}
countries = {'Brazil', 'Japan', 'USA'}
```


### Looking into each of them:
There are multiple forms of collections in Python, the most common ones being:

- [[Chapters/Reference/Data Types/Lists|Lists]] - Similar to "array"s in some other languages, they can contain multiple elements of any type, though preferably you should only store one type inside of them.
	- Examples: `values = [1, 2, 3]`, `animals = ["cat", "dog"]`, `nested_values = [[1, 2], [3, 4]]`
	- Further reading: [[Extra/Libraries/Data Science/Arrays in Python]] for actual arrays, in case you need to work with numpy or come from another programming language and find yourself confusing lists and arrays.
- [[Chapters/Reference/Data Types/Dictionaries|Dictionaries]] - A directed mapping of `key -> value` pairs. The keys must be [[Extra/Abstract Concepts/Object Hashes|Hashable]], but do not worry about it until you get an error related to it. Each key holds one value, and you can efficiently retrieve the value of any key, or iterate through all pairs normally.
	- Examples: `contacts = {"Marcel": "+42 1111-1111", "John": "+42 9999-9999"}`, `person = {"name": "John", "number": "+42 9999-9999"}`, `connections = {"friends": ["Marcel", "John"]}`
- [[Chapters/Reference/Data Types/Tuples|Tuples]] - Similar to lists, but [[Extra/Abstract Concepts/Mutability|Immutable]], and more often used with heterogenous data types (one tuple may have different types, unlike lists that should preferably always store the same type), and tuples have a fixed length as opposed to lists having a variable number of elements.
	- Examples: `person = ('John', '+42 9999-9999')`, `position = (0.5, -1.2)`
- [[Chapters/Reference/Data Types/Sets|Sets]] - Unordered collections of unique items. Much like dictionary keys, the items must be hashable, but what sets them apart is their support for efficiently checking if an item is present in the set, as well as calculating operations such as set Intersection, Difference and Symmetric Difference.
	- Examples: `animals = {"cat", "dog"}`, `countries = {'Brazil', 'USA', 'Japan'}`
- [[Chapters/Reference/Data Types/Range|Range]]: The `range()` function allows for you to create a sequence of integers based on a `start, stop, step` arguments

Please take a brief look at the Reference for each of them, but do not worry about further following their links until you need of them.
It is a lot of information to take in at once, so as long as you have a vague understanding of each of their concepts, that's enough for now - We will dive deeper into them through the Exercises in this chapter and the next chapters to come.

> [!tip] Most important operations
> In particular, make sure you understand how to
> - Add new elements to lists and dictionaries
> - Perform Indexing and Slicing on lists, tuples and strings
> - Remove elements of lists and dictionaries
> - Check if an element is present in a collection

### Exercises
- [[Chapters/Excercises/List Operations 1|List Operations 1]]
- [[Chapters/Excercises/Dictionary Operations 1|Dictionary Operations 1]]
- (Optional) [[Chapters/Excercises/Tuple Operations 1|Tuple Operations 1]]
- (Optional) [[Chapters/Excercises/Set Operations 1|Set Operations 1]]


### Further Reading
These are just the most common of them, and in practice there are a many more you might want to use both in the standard library like [[Extra/Libraries/Standard Library/Modules/Collections|Named Tuples and Counter]], as well as uncountable third-party ones like [[Extra/Libraries/Data Science/Data Frames|Data Frames]].

