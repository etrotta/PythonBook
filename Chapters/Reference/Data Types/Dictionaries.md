### Conceptually

Dictionaries allow for you to create a directed relationship between two types of objects, for example `person name -> person number`, `competition_date -> competition_result`, as well as create records containing multiple fields with different meanings (`field_name -> field_value`).

Taking a look at some examples first, 
```py
# Usage #1: Mapping similar objects (Name -> Number)
contacts = {
	"John": "+00 1111-1111",
	"Mark": "+00 9999-9999",
}

# Usage #2: Detailed information about one object (Field name -> Value)
mark = {"name": "Mark", "number": "+00 9999-9999", "age": 42}
```

The keys have to be a [[Extra/Abstract Concepts/Object Hashes|Hashable]] value such as strings, integers or tuples, but the values can be anything, including lists, other dictionaries or even functions.

Unlike lists and tuples, dictionaries do not care about the positions of their values, only their keys. In the `Usage #2` example, you cannot use `mark[0]` to retrieve mark's name - you have to use `mark["name"]`

### Operations

##### Manipulating values
Dictionaries should always be thought of as a directed mapping of `keys -> values`. You cannot easily retrieve a key given its value or do operations on a subset of their keys the same way you might do slice a list.

In modern Python versions the order of insertion of the elements is maintained, but most of the time you should avoid using dictionaries for problems in which the order matters.

To retrieve the value corresponding to a key, you have to use `dict[key]`, and to set or overwrite a value you have to assign to that key as `dict[key] = value`.
Trying to access a key not present like this will give you an error.

If you want to remove an existing `key -> value` pair, you can use `del dict[key]`

##### Related Functions

Return a a key's associated value or a default value if it's not present: `dict.get(key, default=None)

Operations that mutate them:
- Set a value if it doesn't already exists: `dict.setdefault(key, value)`
- Add all mappings from another dictionary: `dict.update(other)`
- Remove a `key->value` pair and return the associated value: `dict.pop(key)`
- Remove a pair and return it: `dict.popitem()` (Pair selected based on the order of insertion)
- Remove all values: `dict.clear()`

Other operations:
- Create a [[Extra/Abstract Concepts/Shallow and Deep Copies|Shallow Copy]]: `dict.copy()`
- Get the number of pairs in a dictionary: `len(dict)`
- Check if a key is present in a dictionary: `key in dict` (\*technically an expression rather than a function)

Methods that return [views](https://docs.python.org/3/library/stdtypes.html#dict-views):
- A view of its keys: `dict.keys()`
- A view of its values: `dict.keys()`
- A view of its (key, value) pairs: `dict.keys()`

##### Looping

You can loop over dictionaries keys using `for key in dict:`, through their values using `for value in dict.values()` or through both using `for key, value in dict.items()`

We'll cover it in more detail in [[Chapters/Basics/Control Flow/Looping over data|Looping over data]]

### See Also
- Other [[Chapters/Basics/Variables and Functions/Types of Collections|Types of Collections]]
- Although you can easily implement the basic operations required for it it yourself, if you find yourself frequently doing operations over counts of items consider looking into [[Extra/Libraries/Standard Library/Modules/Collections|Collections]]'s Counter type

### Further Reading
For a detailed explanation of what are the 'view' objects, see https://docs.python.org/3/library/stdtypes.html#dict-views

> [!warning] Dictionaries and slices
> As of Python 3.12, you can use the `dict[start:end]` syntax and it will not give you an error - however, that will almost definitely not work as you'd expect.
> 
> In practice, that works almost the same as if you were indexing it with a `(start, end)` tuple, with the only real difference being that it is a `slice()` object instead of a `tuple`.
> 
> In other words, it treats slices as individual, specific keys you can attribute values to, instead of what you would expect from conceptual slices.