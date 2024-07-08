### Conceptually

Sets are a bit unintuitive, so first giving a definition, explaining what each part of it means, then trying to make sense of it:

> **Sets allow for you to create unordered collections of unique hashable items.**

- Hashable: See [[Extra/Abstract Concepts/Object Hashes|Object Hashes]] for more details, but in practice most of the time equals being immutable.
- Unordered: The order of the elements within a set is arbitrary, and it may even differ if you run the exact same program multiple times
- Unique: It only stores whenever an element is present or not, without duplicates - You cannot have a set containing the same integer twice for example

In other words, 
- you cannot store lists or dictionaries with sets, only immutable types such as strings, integers or tuples
- you cannot do any operations related to the order of the elements within a set, as the notion of order is not appliable to them
- `{1, 2, 2}` is the same as `{1, 2}` as `2` is only counted once

They may sound unnecessarily complicated and hard to use, but their biggest advantage are Set Operations - both in the mathematical sense as well as in practice - such as `intersection` or `union`.

Taking a look at some examples, 
```py
lottery_numbers = {10, 20, 30, 40, 50, 60}

my_numbers = {10, 15, 20, 25, 30, 35, 40, 45, 50}

correct_guesses = set.intersection(my_numbers, lottery_numbers)
print(correct_guesses)
```

```py
math_students = {'Mark', 'John', 'Fred'}
history_students = {'Maria', 'Fred', 'Jose'}

all_students = set.union(math_students, history_students)
print(all_students)
```

As you can see, sets are defined using `{}`. This is the same symbol as dictionaries, but usually isn't an issue as dictionaries use `{key: value, key: value}` as opposed to sets just using `{element, element}`...
Except when you want to create an empty set, in which case you have to use `set()` as `{}` is the literal for an empty dictionary

##### Frozen Sets
You can also create immutable sets using `frozenset()`.
They are also hashable, so you can include frozen sets inside of other sets

```py
sub1 = frozenset({1, 2, 3})
sub2 = frozenset({4, 5, 6})
sub3 = frozenset({7, 8, 9})

sequences = {sub1, sub2, sub3}

print({5, 4, 6} in sequences)
print({3, 6, 9} in sequences)
```

### Manipulating values

- Add individual values: `set.add(element)` (effectively does nothing if the set already contains it)
- Add all values from another set: `set.update(other)`
- Remove an individual value: `set.remove()` (error is not present)
- Remove an individual value: `set.discard()` (do nothing if it wasn't present in first place)
- Remove and return an arbitrary element: `set.pop()`
- Remove all values with `set.clear()`
- Create a shallow copy using `set.copy()`
- Check if a value is present: `element in set`
- Count the number of unique items in a set: `len(set)`

### Set Operations

> [!warning] Taking your own notes
> You may want to look up visualizations of set operations in math, many of them don't make much sense only explaining in text.
> Remember to create your own Notes or edit this page to include links you found relevant.

> [!note]+
> You can call `set.method(left, right)`, with `set` being the built-in `set` class, or `left.method(right)` with `left` and `right` both being sets (instances).
> Remember never to define variables with the same name as built-in classes such as `set` or `list`.

##### Creating new sets

- Set Union: Returns all values present in either set, `left.union(right)` or `left | right`
- Set Intersection: Returns all values present in both sets, `left.intersection(right)` or `left & right`
- Set Difference: Returns all values present in `left` that are not present in `right`, `left.difference(right)` or `left - right`
- Set Symmetric Difference: Returns all values present in exactly one of the two sets, `left.symmetric_difference(right)` or `left ^ right`

You can also use `_update` variants for some of them, but see the documentation for that if you are interested in it.

##### Checking properties

- Subset and Superset:
	- Subset: Checks if all elements from `left` are also present in `right`, `left.issubset(right)` or `left < right`
	- Superset: Checks if all elements from `right` are also present in `left`, `left.issuperset(right)` or `left > right`
- Disjoint: Checks that there are no elements in common between `left` and `right`, `left.isdisjoint(right)`

##### Looping

You can loop over set elements using `for element in set:`, but the order will be arbitrary and may change running the same program multiple times even if you make no changes to it.

We'll cover looping in more detail in [[Chapters/Basics/Control Flow/Looping over data|Looping over data]], though not specifically about sets

### See Also
- Other [[Chapters/Basics/Variables and Functions/Types of Collections|Types of Collections]]
- [[Extra/Abstract Concepts/Object Hashes|Object Hashes]]

### Further Reading

> [!note]+ Why the order of elements changes every time you run it
> Copy pasting verbatim from https://docs.python.org/3/reference/datamodel.html#object.__hash__:
> > By default, the [`__hash__()`](https://docs.python.org/3/reference/datamodel.html#object.__hash__ "object.__hash__") values of str and bytes objects are “salted” with an unpredictable random value. Although they remain constant within an individual Python process, they are not predictable between repeated invocations of Python.
> > 
> > This is intended to provide protection against a denial-of-service caused by carefully chosen inputs that exploit the worst case performance of a `dict` insertion, $O(n^{2})$ complexity. See [http://ocert.org/advisories/ocert-2011-003.html](http://ocert.org/advisories/ocert-2011-003.html) for details.
> > 
> > Changing hash values affects the iteration order of sets. Python has never made guarantees about this ordering (and it typically varies between 32-bit and 64-bit builds).
> 
> But TL;DR: Prevent a security vulnerabilities. There are some possible workarounds, but they haven't been implemented, and following the mathematical definition it makes sense for sets to be unordered.