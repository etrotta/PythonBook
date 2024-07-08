### Conceptually
So far we have seen how to perform multiple operations, but always had to manually specify each and every element we are working with.

Loops allow for you to either:
- specify a series of operations that will be executed for each element in a sequence (`for` loops)
- repeat any set of operations an arbitrary amount of times (`while` loops)

They can also be combined with all forms of operations we have learned so far, such as functions and conditional statements.

### For Loops

`for` loops are used to perform a set of operations over each element in a sequence,

```py
for element in sequence:
	function(element)
```

Some examples:
```py
names = ["Mark", "Luna", "Kai"]
for name in names:
	print(f"Hello, {name}!")
```
```py
for i in range(10):
	print(i, i ** 2)
```

In practice, they are essentially doing:
```py
element = sequence[0]
function(element)
element = sequence[1]
function(element)
element = sequence[2]
function(element)
...
element = sequence[-1]
function(element)
```

> [!tip]
> You can also use [[Chapters/Reference/Operations/Indexing and Slicing#^00e56d|Unpacking]] inside of loops.
> There are some built-in functions meant to be used alongside that, in particular `enumerate(list)` to get the index of each element in addition to the element itself, and `zip(a, b, c)` to iterate over multiple lists together. Check their documentation to learn more about them.

### While Loops

`for` loops are useful when you need to perform an operation for each element of a sequence, but you won't always have a sequence to operate on - sometimes you'll need to repeat a set of operations until a condition is cleared, or even forever.

When you want to repeat an operation an undetermined amount of times, you may want to use `while` loops instead.

Some examples:
```py
i = 0
while (i ** 2) < 1000:
	i = i + 1

print(i, i ** 2)
```

```py
target = 55
numbers = list(range(100))

left = 0
right = len(numbers)

i = (left + right) // 2
while numbers[i] != target:  # '! =', might show as a crossed == in some fonts
	if numbers[i] > target:
		right = i
	elif numbers[i] < target:
		left = i
	i = (left + right) // 2
	print(i, numbers[i])

print(i, numbers[i])
```

### Related Statements: `break` and `continue`

The `break` and `continue` statements can be used inside of `for` or `continue` loops.

`continue` statement are used to skip the current iteration, and `break` statements are used to exit out of the loop.

Some examples:
```py
for i in range(10):
	if i % 3 == 0:
		continue
	print(i)
```

```py
names = []
while True:
	name = input("""Enter a name, or "end" to exit the loop: """)
	if name == "end":
		break
	names.append(name)

print(names)
```

In practice, you'll rarely see either of them in `for` loops, but they're used fairly often with `while` loops, specially `while True:` which will only exit if you use a `break` statement.

Also remember that if you `return` inside of functions, it'll exit the loop and everything else inside of the function. If you want to return multiple values, odds are you should just append them to a list then return that list, but you can also look into [[Unorganized/MISSING|Generators]] later for functions that can "return" multiple times

### Exercises

- [[Chapters/Excercises/Numeric Operations 3|Numeric Operations 3]]
- [[Chapters/Excercises/Numeric Operations with Collections 1|Numeric Operations with Collections 1]]

### See Also

[[Unorganized/MISSING|List comprehensions]], looping over and creating a new list in a single line for simple operations.

> [!warning] These are both Advanced concepts and not required for the Main Chapters

[[Chapters/Reference/Operations/Recursion|Recursion]], having a function call itself to solve problems in multiple steps
[[Chapters/Basics/Variables and Functions/Generators|Generators]], having a function "return" multiple times