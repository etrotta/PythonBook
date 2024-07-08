> [!warning] This page is optional, and fairly advanced

### Conceptually

Functions are able to return values, but a function may only return once.

If you want to return a collection of values, the main way you would do it is creating a list, appending to it and returning it instead, but there are some cases in which that would be impractical.

Generators allow for you to create functions that "return" multiple times by yielding values, pausing their execution until you request the next value, and could even be made to yield infinite values depending on how you use them.

Take a look at [[Unorganized/MISSING|Eager vs Lazy]] if you haven't yet.

```py
def cumulative_sum(values):
	total = 0
	for value in values:
		total += value
		yield total

generator = cumulative_sum(range(10))
print(generator)
print(list(generator))
# Generators become Exhausted after you iterate through them once
print(list(generator))

generator = cumulative_sum(range(10))
print(next(generator))
print(next(generator))
print(next(generator))
```

### Generators themselves

A generator keeps track of the state it's in, as if you paused the execution of a function.
```py
def example():
	print("Start execution")
	yield 1
	print("Point A")
	yield 2
	print("Point B")
	return 3

gen = example()
print("Point X")
next(gen)
print("Point Y")
next(gen)
print("Point Z")
next(gen)
# StopIteration error as there is no value for it to yield next
```

They yield the values one at a time as you request them, but other than that they're similar to functions in regards of how you define them and how their scope works.

### Yielding values
Instead of `return`, generators use the `yield` statement to "return" values, typically one at time.
You can use `next()` to run a generator until it yields the next value in order to work with a single value at a time, or pass it to `list()` or a `for` loop to go through all remaining values.

```py
def example():
	yield 1
	yield 2
	yield 3

gen = example()
print(next(gen))  # 1, the first value it returns
print(list(gen))  # [2, 3], all remaining values
print(list(gen))  # [], since it's already 'exhausted'
print(list(example()))  # [1, 2, 3], all values
```
```py
def pow_gen(iterator, power):
	for val in iterator:
		yield val ** power

print(list(pow_gen(range(10), 2)))
```

##### Yield from
You can also use `yield from ...` to yield all values from another iterator, akin to `for element in ...: yield element`
This also allows for you to create recursive generators,

```py
def chain(first, second):
	yield from first
	yield from second

print(list(chain([1, 2, 3], [4, 5, 6])))
```

```py
def flatten(iterator):
	for element in iterator:
		if isinstance(element, (list, tuple)):
			yield from flatten(element)
		else:
			yield element

for element in flatten([1, [2], 3, [4, 5, [6, [7, 8]], [9]], 10]):
	print(element)
```


##### Exhausted generators

After you iterate through all values a generator has to return, they become "exhausted". That's just a convention to say it has nothing left to yield.
- If you try to iterate through it, you'll get nothing
- If you call next() on it, you'll get a StopIteration error

```py
def generator():
	yield

gen = generator()
for _ in gen:
	pass

print(list(gen))
print(next(gen))  # Not even printed, just raises an StopIteration Exception
```

If your generator has a `return` statement, the exception will contain whatever is returned

```py
def generator():
	yield 10
	return 42

gen = generator()

print('A', next(gen))

try:
	print('B', next(gen))
except StopIteration as err:
	print('X', err.args)

try:
	print('C', next(gen))
except StopIteration as err:
	print('Y', err.args)
```

### Sending values

> [!warning]
> You may want to use a custom class (see: OOP) instead if you feel like using this to store and manage state

Similarly to how generators can output values multiple times, they can also receive inputs multiple times.

By calling `send(generator, value)` instead of calling `next(generator)`, you can give a value back to it.

```py
def add(iterator, value):
	for element in iterator:
		print(element, value)
		value = yield element + value
		print(element, value)

generator = add([10, 16, 34], 6)
print(next(generator))
# print(generator.send(None))  # You can send `None` to act as if you called `next()`, but you can only send actual values after it reaches a `yield` statement
print(generator.send(100))
print(generator.send(200))
print(generator.send(300))
```
```py
def add(iterator, value):
	for element in iterator:
		returned = yield element + value
		if returned is not None:
			value = returned

generator = add([10, 16, 34], 6)
print(list(generator))  # Would give an error with the first, as `list()` sends None for each element
```

### Exercises

- Reimplement some functions from [[Extra/Libraries/Standard Library/Modules/Itertools|Itertools]] or `more-itertools`
- Create a generator for yielding Excel column names.
	- Taking it even further, use `send()` to return lists of columns of varying lengths instead of a single column at a time
	- Taking it even further, support negative numbers to 'go back'
