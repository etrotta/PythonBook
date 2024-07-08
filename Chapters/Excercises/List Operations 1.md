### Exercise 1: Manipulating Lists

Use slicing, indexing and list operations to transform the following lists into the desired results:

```py
numbers = [0, 1, 2, 3, 4, 5, 6, 7]
to_be_added = [20, 30]

assert result == [6, 5, 4, 30, 20]
```

```py
letters = ['A', 'B', 'C', 'D', 'E']

assert result == ['A', 'E', 'C', 'D']
```

There are many valid ways to go about it - Any way that reaches the desired results is a valid solution.

> [!note] About `assert`
> The `assert` statement is used to test if an expression is True, or in this case, if the sequence variable is equal to the expected value.
> - If the expression is True, Python will just continue the program as normal
> - If the expression is False, Python will raise an Exception telling you that something went wrong
> 
> We'll learn more about it in Testing later on

### Exercise 2: Fibonacci (Part 1)

Calculate the first 11 numbers of the [Fibonacci sequence](https://en.wikipedia.org/wiki/Fibonacci_sequence), appending them to the list at each step

```py
sequence = [0, 1]

# YOUR CODE GOES HERE

assert sequence == [0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55]
```

> [!note]
> You will come back to this Exercise once you learn how to use loops, in order to calculate more elements of the series.
> Remember to document your code!
