### Exercise 1 - Linear equation

Given a equation $y = ax + b$, calculate the value of `y`.

```py
x = 5
a = 10
b = 4

y = ...

print(f"The value of y for `{a}{x} {b:+}` is {y}")
```

### Exercise 2 - Quadratic equation

Given a equation $y = ax**2 + xb + c$, calculate the value of `y`.

```py
x = 5

a = 1
b = -5
c = 6

# Your code goes here
```

### Challenge - Quadratic formula

Try to calculate the roots of a quadratic equation $ax^2+bx+c = 0$ with Python through the quadratic formula:

$$\Delta = {b^2 - 4ac}$$
$$x = \frac{{-b \pm \sqrt{\Delta}}}{2a}$$

For example, the roots of $x^2-5x+6$ are $2$ and $3$,
$$\Delta = {(-5)^2 - 4*1*6} = 25 - 24 = 1$$
$$x = \frac{{5 \pm \sqrt{\Delta}}}{2} = \frac{{5 \pm \sqrt{1}}}{2}$$
$$x_1 = \frac{5 - 1}{2} = 2$$
$$x_2 = \frac{5 + 1}{2} = 3$$

Code Template: 
```py
# Feel free to change the values for `a`, `b` and `c` to test various cases.
a = 1
b = -5
c = 6
print(f"Calculating the roots for `{a}*(x**2) + {b}*x + {c} = 0`")

# YOUR CODE GOES HERE

```

Do not worry about cases in which $\Delta=0$ or $\Delta<0$ for now, we will cover how to handle that in a different Chapter later, and its Exercise will be building upon your solution to this problem.

> [!info] Comments
> You can use `#` to add comments to your code, like you can see in the Code Template.
> The Python interpreter will ignore them while running your code, but they are useful for humans reading your code - this includes both other developers you may be collaborating with, as well as yourself looking at your own code in the future.
> 
> We will build upon this solution in the future, so remember to add comments for yourself if required!

> [!tip]- If you get stuck
> Use different variables for each solution, `x1` and `x2`, performing different operations for each.
> Make sure you're using parenthesis to specify the order of operations.
> Breakdown the problem into smaller steps.
> Remember to check the Reference [[Chapters/Reference/Operations/Numeric Operations|Numeric Operations]] to look for the operations you need at each step.

> [!warning]- Solution
> 
> If you are stuck even after reading the Hints, try taking a short break then look at it again from a different angle first
> 
> > [!error]- Reveal
> > > The first step you should take is to calculate delta,
> > > `delta = b**2 - 4*a*c`
> > > Then you can add more variables to make it clearer, or go straight to the solution:
> > >  `x1 = (-b - delta**0.5) / 2*a`
> > >  `x2 = (-b + delta**0.5) / 2*a`
> > > After that, remember to print your result
> > > `print(f"The roots are: {x1} and {x2}")`

