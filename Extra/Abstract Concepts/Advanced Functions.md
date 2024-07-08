
%% I'm painfully aware that this page still requires a lot of work, specially thinking of better examples %%

### Benefits of using Functions

Functions allow for you to define custom operations, with their main advantages being
- Reusing your own code: By calling a function, you can easily apply operations without having to type all of their instructions.
- Using code written by others: Instead of having to define them yourself, you can use sets of operations created by others by importing their code into your program, and calling their functions.
- Customizing these operations: You can change the behavior of functions by changing the arguments you use when calling them, whenever it leads to a small change in what the function is doing or a nearly completely different operation.
- Make your code more readable: By separating your code into small or medium sized functions and documenting each of them, it becomes a lot easier to understand what your code is doing at each step than having everything in a single place.

In this Extra chapter, we will see how you can take advantage of some advanced features to further improve the customizability and readability of your code.

### Optional Parameters

Oftentimes you'll want to have default values for your parameters, so that the user may include them or use the default values. 

```py
def linear(x, a=1, b=0):
	return x*a + b

assert linear(10) == 10
assert linear(10, 2) == 20
assert linear(10, 2, 5) == 25

def sum_string(string, separator=","):
	numbers = map(float, string.split(separator))
	return sum(numbers)

assert sum_string("1,2,3") == 6
assert sum_string("1;2;3;4", ';') == 10
```

### Keyword Parameters

By default, when calling functions you can specify the arguments by position or by name:

```py
def linear(x, a=1, b=0):
	return x*a + b

assert linear(10, a=2, b=5) == 25
assert linear(10, b=5) == 15
```

But you can also require for them to be specified as positional-only or keyword-only by including `/` or `*` in the parameters definition,

```py
# Require for `x` to be specified as a positional argument
def linear(x, /, a=1, b=0):
	return x*a + b

# Require for `a` and `b` to be specified as keyword arguments
def linear(x, *, a=1, b=0):
	return x*a + b

# Require for `x` to be positional, `y` let be positional or keyword, require `z` to be a keyword argument
def func(x, /, y, *, z):
	...
```

### Variadic Functions

Functions can also be made to receive any number of arguments, collecting extra positional arguments as a tuple and keyword arguments as a dict.

```py
def product(*arguments):
	total = 1
	for number in arguments:
		total *= number
	return total

assert product(2, 3, 5) == 30

def maximum_key(**keyword_arguments):
	max_key = None
	maximum = float('-inf')
	for key, value in keyword_arguments.items():
		if value > maximum:
			max_key = key
			maximum = value
	return max_key

assert maximum_key(a=1, b=3, c=2) == 'b'
```
%% you can do that with the built-in `max` function by the way, `max(dict.items(), key=lambda t: t[0])` %%

You can also unpack tuples, lists and dictionaries into separate arguments:

```py
def linear(x, a=1, b=0):
	return a*x + b

values = (10, 2, 5)
assert linear(*values) == 25
# works the same as calling `linear(10, 2, 5)`

partial_values = [10, 5]
assert linear(*partial_values, 7) == 57
assert linear(*partial_values, b=7) == 57

values_keyword = {'x': 10, 'a': 2, 'b': 5}
assert linear(**values_keyword) == 25
```

Combining these two, you can also pass arbitrary arguments from one function to another

```py
def quadratic(x, /, a, b, c):
	return a*x**2 + b*x + c

def test_values(values, /, function, *args, **kwargs):
	results = {}
	for value in values:
		results[value] = function(value, *args, **kwargs)
	return results

values = (1, 2, 2.5, 3, 4, 5)
args = [1, -5]
kwargs = {'c': 6}
test_values(values, quadratic, *args, **kwargs)
assert test_values(values, *args, **kwargs) == {1: 2, 2: 0, 2.5: -0.25, 3: 0, 4: 2, 5: 6}

```

> [!note] If you cannot understand what is going on
> That is to be expected and I would be more concerned if you did understand it the first time you look at it with no prior experience.
> 
> You should already be used to it by the time you reach this Extra Chapter, but reenforcing: You're supposed to run the examples yourself and play around with them, from adding `print()` statements all over the place to [[Extra/Ecosystem/Tooling/Using the Debugger|Using the Debugger]] to analyze in detail what is happening.
> 
> You should also try to edit it a bit to see if you can understand it well enough to work with it, and try to implement something else using the same concepts to do something different.

> [!warning]- Still stuck?
> For that example in particular, it will first iterate over each value, then call the function using that value + the extra arguments you passed to the function, reusing the same extra args/kwargs for each call.
> 
> Try adding `print(x, a, b, c)` inside of the `quadratic` function or `print(value, args, kwargs)` inside of the `for ...:` loop