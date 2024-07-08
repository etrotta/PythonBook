### Overview

You can apply both Indexing and Slicing operations on many types of sequences in Python, such as strings, lists and tuples.

Indexing lets you retrieve individual elements, such as the `first`, `nth`, `last` etc. element of a sequence.

Slicing is useful when you want to create a copy excluding some elements, for example `all except the first element` or `every other element`, or splitting into parts such as `the first half and the second half`

```py
first_element = sequence[0]
nth_element = sequence[n]
last_element = sequence[-1]
```

```py
all_except_first = sequence[1:]
every_other = sequence[::2]

middlepoint = len(sequence) // 2
first_half = sequence[:middlepoint]
second_half = sequence[middlepoint:]
```

### Indexing

To index a sequence, you can use the `sequence[index]` syntax. When doing this, `index` must be an integer representing the position in the sequence, with the first element being `0`, followed by `1`, `2` and so on.
You can also use negative numbers to count from the end, with `sequence[-n]` behaving the same as `len(sequence) - n`, so `-1` represents the last element.

```py
example_string = "ABCXYZ"
example_list = ["A", "B", "C", "X", "Y", "Z"]
# In both cases, len(sequence) = 6


# Index:           0 |  1 |  2 |  3 |  4 |  5
# Character:       A |  B |  C |  X |  Y |  Z
# Negative Index: -6 | -5 | -4 | -3 | -2 | -1

```

If you try to access an element that does not exists (in a position beyond the sequence's length), you'll get an error.

### Slicing

Slicing is used to create a [[Extra/Abstract Concepts/Shallow and Deep Copies|Shallow copy]] of a sequence, containing only some of the original elements.
You can specify the `start` index of the slice, the `stop` index of the slice and the `step` size of the slice.
- Slices will start from the `start` position, including it
- Slices will stop right before the `stop` position, excluding it
- Slices will only include every `step`th element.

If you don't specify them, they'll default to [[Chapters/Reference/Data Types/Special Values#^3bff32|None]] and behave as:
- `start` will be the beginning of the list
- `stop` will be the end of the list, including the last element
- `step` will be `1`, including all elements

You can use negative numbers for the `start` and `stop`, and it'll work the same as it would for Indexing (`len(sequence) - n`).
You can also use a negative `step` to reverse the order of the elements in the slice, in which case the default values for `start` and `stop` also change to the opposite ends if not specified.

Some examples:
```py
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8]
len(numbers) == 9

numbers[0:5] == [0, 1, 2, 3, 4]
numbers[3:7] == [3, 4, 5, 6]

numbers[::2] == [0, 2, 4, 6, 8]
numbers[::3] == [0, 3, 6]

numbers[::-1] == [8, 7, 6, 5, 4, 3, 2, 1, 0]
numbers[::-3] == [8, 5, 2]

numbers[-5:-2] == numbers[4:7]
numbers[-5:-2] == [4, 5, 6]

numbers[-2:-5:-1] == numbers[7:4:-1]
numbers[-2:-5:-1] == [7, 6, 5]
```

There is also a `slice` function you can use if you want to create and store a slice for later usage, though it's very rarely used.
```py
every_other = slice(None, None, 2)
numbers[every_other] == numbers[::2]
```

%%
Author's Note:
I think I've only ever needed to call `slice()` explicitly when working with `pandas`'s `MultiIndex`es for something like

```py
idx = [(outer, inner) for outer in (1, 2, 3) for inner in (1, 2, 3)]
df = pd.DataFrame(
	data = {'X': range(9)},
	index=pd.MultiIndex.from_tuples(idx, names=['lv1', 'lv2']).sort_values(),
)

>>> df.loc[(slice(None, 2), slice(2, None)), 'X']
lv1  lv2
1    2      1
     3      2
2    2      4
     3      5
```

In which case, using the normal `[::]` syntax was not an option (just Syntax Error)

If this makes no sense for you, yeah don't worry, you can delete this comment if it's in the way of your own notes, or otherwise distracting you

If you have never touched pandas Multi Index before, **DO NOT DIVE INTO THAT RABBIT HOLE** unless you truly need of it.

%%
### Overwriting values

When working with [[Extra/Abstract Concepts/Mutability|mutable]] data types, you are typically able to overwrite values by assigning to an index or to a slice.

When assigning to an Index, it'll just overwrite the value at that specific index

When assigning to a Slice, it'll remove the original slice, then add the elements you assigned to it at that position. For most types, the number of elements removed and added don't have to match.

```py
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8]

numbers[0] = 99  # Overwrite a single Index
print(numbers)

numbers[2:4] = [20, 30]  # Remove and add same amount of elements
print(numbers)
numbers[4:7] = []  # Remove without adding any new elements
print(numbers)

numbers[1:1] = [100, 110, 120]  # Add without removing any
print(numbers)
```

Trying to do that on a immutable data type such as a string or a tuple will give you an error - you should use other methods such as manually slicing each part then concatenating back together in such cases.

### Unpacking

^00e56d

If you want to extract multiple positions into their separate variables, you can use unpacking instead of manually specifying each position.

It also allows for you to separate only some values, then collect the rest into a list by prefixing `*` before a variable.

Examples:
```py
numbers = [10, 20, 30, 40, 50]

a, b, c, d, e = numbers
a == 10
d == 40

first, *middle, last = numbers
first == 10
middle == [20, 30, 40]
last == 50

x, y, z = (1, 2, 3)
x == 1
y == 2
z == 3

x, z = (z, x)

z == 1
x == 3
```

### See Also
We'll cover loops in [[Chapters/Basics/Control Flow/Looping over data|Looping over data]] later, which you'll use if you want to perform operations on every element of a sequence.

### Further Reading

If you are using data structures provided by third-party libraries such as multi dimensional [[Extra/Libraries/Data Science/Arrays in Python|Arrays]], Tensors or [[Extra/Libraries/Data Science/Data Frames|Data Frames]], check their respective Extra Pages or the documentation of their libraries - They'll oftentimes support more advanced slicing operations.
