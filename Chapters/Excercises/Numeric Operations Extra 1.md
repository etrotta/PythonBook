> [!warning] This is not required to progress through the Main Chapters

### Exercise 1 - Fibonacci

Create a recursive function to calculate the Fibonacci sequence 

$$
F_n = \begin{cases} 0 & \text{if } n = 0 \\ 1 & \text{if } n = 1 \\ F_{n-1} + F_{n-2} & \text{if } n > 1 \end{cases}
$$

> [!tip]
> Use the `functools.cache` decorator to cache results, otherwise it'll take `2 ** n` time to calculate the result

```py
from functools import cache

@cache
def fib(n):
	...

assert fib(0) == 0
assert fib(1) == 1
assert fib(2) == 1
assert fib(3) == 2
assert fib(4) == 3
assert fib(5) == 5
assert fib(6) == 8
assert fib(7) == 13

print(fib(1000))
print(fib.cache_info())
```
