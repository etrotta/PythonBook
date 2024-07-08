### Conceptually
Lists are a common way of working with multiple values within the variable, letting you keep track of any number of elements without having to create separate variables for each of them, as well as serving as a base for doing operations on each of them.

A lot of the time when you have multiple variables referring to multiple instances of the same type, you may want to consider using a collection like a list or a dictionary instead.
Some use cases include storing data about multiple books, persons or tests scores.

To create lists, you have to wrap multiple values within square brackets (`[]`) and separate each of them using commas (`,`)

Examples:
```py
books = ['Sword Art Online', 'Overlord', 'Ruination', 'Tenken', 'Tensura']

test_scores = [7, 8, 6, 9, 7]
```

### Operations

##### Indexing and Slicing

To retrieve an element out of a list, use `[index]`, with the first element being at the index 0.
To create a new list containing multiple elements of this list, you can use slicing via `[start_index:end_index]` (including `start_index`, but excluding `end_index`)

```py
print(books[0])
print(books[1])
print(books[2])

print(books[1:])  # All values from index 1 until the end of the list
print(books[:2])  # All values from the start until index 2 (excluding 2)
print(books[1:3])  # All values between 1 and 3 (excluding 3)

# You can also use negative indexes to get values from the end:
print(books[-1])
```

You can also mutate lists by assigning elements to specific indexes, or overwriting slices.
When overwriting slices, it will first remove the entire selection you specified, then insert the values at that position - the number of inserted elements does not have to match the number of removed elements.

```py
# Overwrite the first book
books[0] = "Gun Gale Online"
print(books)

# Remove the last two, and add a new one
books[-2:] = ["TenTen Kakumei"]
print(books)
```

Read [[Chapters/Reference/Operations/Indexing and Slicing|Indexing and Slicing]] for more details.

##### Operators

- Check if a list contains a given element: `element in list` (\*technically an expression rather than a function)
- Concatenate lists (create a new list containing all elements from the both lists): `left + right`, e.g. `[1, 2] + [3, 4] == [1, 2, 3, 4]`
- Repeat a list multiple times (concatenating copies of it): `list * integer`
	- Be careful: This creates [[Extra/Abstract Concepts/Shallow and Deep Copies|Shallow Copies]] of any mutable objects within the list, which can lead to bugs when using nested lists

##### Functions

To modify lists, you can:
- add individual elements using `list.append(element)`
- add an element at a specific index by using `list.insert(index, element)`
- add all values from another list at once using `list.extend(other)`
- remove elements from the end of the list using `list.pop()` without arguments
- remove elements by position using `list.pop(index)`, specifying the index
- remove elements by value using `list.remove(element)`
- remove all values from a list using `list.clear()`
- sort the list in place by using `list.sort()`
- inverse the order of the elements within the list by using `list.reverse()`

There are also the following methods and other functions that do not modify the list:
- Get the position of an element using `list.index(element)` (\*if it appears multiple times, it'll return the first index)
- Count the number of elements in the list using `len(list)` 
- Count the number of times a given element appears in the list using `list.count(element)`
- Create a [[Extra/Abstract Concepts/Shallow and Deep Copies|shallow copy]] using `list.copy()`
- Create a sorted shallow copy using `sorted(list)` (without modifying the original list)

```py
reincarnations = ["Slime", "Spider"]
reincarnations.append("Skeleton")
print(len(reincarnations), reincarnations)
print(reincarnations.index("Spider"))

reincarnations.extend(["Sword", "Vending Machine"])
print(len(reincarnations), reincarnations)

print(reincarnations[0], reincarnations[-1])
print(reincarnations[1:4])

# pop() also returns the removed element
print(f"Removing top element (1/2): {reincarnations.pop()}")
print(f"Removing top element (2/2): {reincarnations.pop()}")
print(reincarnations)
```

##### Looping

We'll covert this in more detail in later on in [[Chapters/Basics/Control Flow/Looping over data|for loops]], but `for` loops are used when you want to perform operations on each element of a list.

Do not worry about it yet, but a small preview of it:
```py
test_scores = [7, 8, 6, 9, 7]
total = 0
for score in test_scores:
	total += score

print(f'Sum of scores: {total}')
print(f'Average score: {total / len(test_scores):.1f}')
```

```py
names = ['Sr. Bird', 'Mr. Cat', 'Dr. Dog']
scores = [14, 12, 13]

# "zip" will also be seen in that chapter
print(f"{'Name':<10} | Score")
for name, score in zip(names, scores):
	print(f"{name:<10} | {score}/10")
```

### Further Reading

- You should understand [[Chapters/Reference/Operations/Indexing and Slicing]] fairly well by the time you are done reading this page the first time. Not an Extra, just separated because it's used for many collections - Do read it if you haven't yet.
- [[Chapters/Basics/Control Flow/Looping over data]] will be covered later (and soon), so don't worry about them yet, but you can check if you want.
- You may want to understand the difference between [[Extra/Abstract Concepts/Shallow and Deep Copies]]
- See also the other [[Chapters/Basics/Variables and Functions/Types of Collections|Types of Collections]]
