# Named Tuples

[[Chapters/Reference/Data Types/Tuples|Tuples]] are commonly used to represent similar elements, but it can be inconvenient to refer to their elements based on their position.
Named tuples let you assign names to each position instead,

```py
from collections import namedtuple

Book = namedtuple("Book", ('name', 'pages', 'author'))

example_book = Book("Sword Art Online 1: Aincrad", 264, "Reki Kawahara")

print(example_book)
print(example_book.author)
```

If this sounds like it overlaps with dictionaries (and more specially [TypedDict](https://docs.python.org/3/library/typing.html#typing.TypedDict)), well yeah, it does.

Tuples can be marginally more efficient than dictionaries, but if you care about efficiency that bad, you should likely be using [[Extra/Libraries/Data Science/Arrays in Python|Arrays]], [[Extra/Libraries/Data Science/Data Frames|Data Frames]] or [[Extra/Libraries/Databases/SQLite|Databases]] instead of working with the data within Python.

# Counter

Effectively a specialized type of dictionary, Counter can be used to keep track of the number of times each element appears in a sequence, as well as let you do calculations over every count.

```py
from collections import Counter

letters = ['a', 'b', 'b', 'c', 'c', 'c']

counter = Counter(letters)

print(counter)
print(counter['b'])
print(counter['z'])
print(counter.most_common(2))

counter += {"a": 4, "b": 1, "d": 2, "c": -1, "z": -1}
print(counter)
```

# Double ended queues

Not to be confused with [Heap queue](https://docs.python.org/3/library/heapq.html) nor [queues for communication between threads](https://docs.python.org/3/library/queue.html), `collections.deque` provides simple double ended queues, that allow for you to access and append to either end of it in O(1) in expense of accessing elements in the middle taking O(n)

(If you try to add insert or remove elements at the index 0 of a normal list, Python will have to move everything that's already in the list by one position - If you need of that for some reason, consider using Queues)

They are a bit more niche, so check the official documentation if you want to see examples of them.

# See Also
[[Extra/Libraries/Standard Library/Modules/Dataclasses|Dataclasses]] let you define classes using a fairly simple syntax, while preserving the customizability of normal classes.

If you need to work with large amounts of data, you probably should be using [[Extra/Libraries/Data Science/Data Frames|Data Frames]] or [[Extra/Libraries/Databases/SQLite|Databases]]

# Further Reading

Official Documentation: https://docs.python.org/3/library/collections.html
