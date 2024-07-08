### Conceptually
Functions allow for you to define your own operations by building on top of existing operations, letting you reuse code instead of typing all steps you need whenever you have to repeat the same operation.

In particular, you should use them often to:
- Reuse operations you do frequently: By calling a function, you can easily apply saved operations without having to type all of their instructions.
- Keep your code readable: By separating your logic into small functions and documenting each of them, it becomes a lot easier to understand what your code is doing at each step than having everything in a single place.

```py
def mean(x, y, z):
	"Calculate the mean of three values"
	return (x + y + z) / 3

result_1 = mean(1, 2, 3)
result_2 = mean(10, 100, 1000)
result_x = mean(x, y, z)
```

Read [[Chapters/Reference/Operations/Creating Functions|Creating Functions]] to understand how to define functions and call them.

### Variable Scope

When working with functions, variables defined within the function only exist inside of the function.

```py
def foo():
	x = 10

foo()
print(x)  # Error!
```

When using functions, if you feel like you want to define variables that last beyond their scope, use `return` statements instead such as
```py
def foo():
	x = 10
	return x

x = foo()
print(x)  # prints 10
```

### Next Steps
After reading the Reference page,

Once you get the idea, try defining a function or two of your own, then proceed to the Exercise [[Chapters/Excercises/Numeric Operations 2|Numeric Operations 2]] to practice it.

After you are done with the exercise, follow on to the Chapter [[Chapters/Basics/Variables and Functions/Types of Collections|Types of Collections]], which will explain how to work with collections of values instead of only dealing with individual numbers or strings.

You might want to come back to this page and dive into the Further Reading section after you complete the Basic Chapters

### Further Reading

- As we will see more in detail in future Chapters, in Python abstracting a series of operations into functions also allows for you to pass the those operations for other tools to execute them later.
	You can take a look at [[Extra/Abstract Concepts/Functions as Variables]] to see some advanced use cases of this aspect of functions, but they should still be way too complicated for you at this point in time.
- Functions can also receive arguments by name, have optional arguments, as well as accept any number of arguments. You can read more about it in [[Extra/Abstract Concepts/Advanced Functions|Advanced Functions]].
- [[Chapters/Basics/Variables and Functions/Generators|Generators]] are functions that can "return" multiple times, but you should only look into them after you're comfortable with collections such as lists. See [[Unorganized/MISSING|Lazy vs Eager]] before looking into them.