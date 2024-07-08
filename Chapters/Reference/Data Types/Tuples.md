### Conceptually
Tuples are similar to lists, with the biggest difference being that they are [[Extra/Abstract Concepts/Mutability|Immutable]] and as such have a fixed width.

While lists commonly represent a collection of similar objects, tuples are more often used to represent one object that has multiple attributes, for example a person could be represented as a (name, age) tuple such as `("John", 20)`

If a list lets you store multiple books in a single variable, then a tuple lets you store more information about a single book within the same variable.

```py
example_book = ("Sword Art Online 1: Aincrad", 264, "Reki Kawahara")

# format: (book_name, pages_count, author)
# type annotation: tuple[str, int, str]
print(example_book)
print(example_book[0])
name, pages, author = example_book
print(author)

# and you can put them inside of other collections like lists or dictionaries
books = [book_1, book_2, ...]
```

To create tuples, you have to wrap multiple values within square brackets (`()`) and separate each of them using commas (`,`)

Technically it is the commas that define a tuple, rather than the `()`, but most of the time you should include `()` to make it clearer.

Examples:
```py
lottery_numbers = (1, 2, 3, 42, 37, 7)
# Works the same as
lottery_numbers = 1, 2, 3, 42, 37, 7
```

If it feels like this overlaps greatly with lists and dictionaries, it is because it does - much of the time it's up for you to decide which you'd rather use for a given case, sometimes with no wrong choice.

### Operations

They support relatively few operations - Tuples are mainly used to store data in a more structured way, not actually operate on that data.
That also gives them the advantage of being [[Extra/Abstract Concepts/Object Hashes|Hashable]]

##### Indexing, Slicing and Unpacking

Tuples support these three operations the same way as they work on lists, but in practice you'll see Unpacking used much more often with tuples, and Slicing almost never used.

Read [[Chapters/Reference/Operations/Indexing and Slicing|Indexing and Slicing]] to see how each of them work, including unpacking.

##### Tuple Functions

The only functions they support are
- `element in tuple` (\*technically an expression rather than a function)
- `tuple.index(element)`
- `tuple.count(element)`
- `len(tuple)`

Which work the same as they do for lists.
You can use `sorted()` to create a sorted list based off a tuple.

As tuples are immutable, you cannot modify them. Much like strings, you would have to create a new tuple instead if you wanted to modify one, though you probably should be using a list instead if you want to modify it.

### Further Reading

- You had better understand [[Chapters/Reference/Operations/Indexing and Slicing]] fairly well by now.
- See also the other [[Chapters/Basics/Variables and Functions/Types of Collections|Types of Collections]]
- For even more types of collections, including Named Tuples, see [[Extra/Libraries/Standard Library/Modules/Collections|Collections]]
