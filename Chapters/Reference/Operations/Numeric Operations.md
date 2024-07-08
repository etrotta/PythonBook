### Conceptually
Numbers may represent nearly any value you have to work with, and a lot of programs will need to do operations on them.
You do not need to be extremely proficient at math to program, but it can be useful in many areas.

Some more complex examples include determining the position and velocity of objects when developing games, or simulating things and calculating statistics in scientific programs (although oftentimes third-party libraries will implement these operations for you).

### Arithmetic operations:
All of these operations are supported for [[Chapters/Reference/Data Types/Numeric Data Types|Integers, Floats, Complex numbers and Booleans]] as well as [[Extra/Libraries/Standard Library/Modules/Decimal and Fraction|Decimal and Fraction]]

- Addition: `x + y`
- Subtraction: `x - y`
- Multiplication: `x * y`
- Power: `x ** y` or `pow(x, y)`
- - Note: Raising a number to `** (1/2)` is the same as calculating its square root
- Division - There are two forms of division in Python: 
- - Integer division - The result is floored down to the nearest integer: `x // y`
- - Real division - The result is always a float: `x / y`
- Modulo: `x % y`. This operation is essentially the remainder of the division, e.g. `19 % 5 == 4`
- - Note: You can use the `divmod` function as `quotient, remainder = divmod(x, y)` to calculate both the integer division as well as the remainder in the same operation.

### Observations
Make sure that you use `*` when you want to perform multiplications.
If you write it like you might in math, such as `2(3+4)` or `2x`, Python will give you an error like `TypeError: 'int' object is not callable` or `SyntaxError`

### Other Functions
- Absolute value: `abs(x)`, converts negative numbers to positive, and does nothing for positive numbers or zero.
- Rounding floats: `round(x)` converts a float to the nearest integer. If it's `.5`, it will pick the closest multiple of 2.
- Flooring floats: `int(x)` converts a float to the closest integer towards 0. For positive numbers, that's the same as rounding down, but for negative numbers it rounds up.
- Converting to and from strings:
	- `int(string)` for decimal numbers or `int(string, 2)`/`int(string, 16)` for binary or hexadecimal numbers
	- `str(integer)`, `hex(integer)` or `bin(integer)` for converting to strings

### See also:
- Nearly all types in Python support [[Chapters/Reference/Operations/Logical Operations|Logical Operations]], including numbers
- There are also [[Extra/Python Operations/Bitwise Operations|Bitwise Operations]], but this book will not cover them as part of the main Chapters. Just be careful not to use `x ^ y` instead of `x ** y`, as these are two different operations.
- For more advanced operations, you may need to use the [[Extra/Libraries/Standard Library/Modules/Math|Math]] module of the standard library.
- If even the math module does not supports what you're trying to do, then you may need to use third-party libraries such as [[Extra/Libraries/Data Science/Numpy|Numpy]] or [[Extra/Libraries/Data Science/Scipy|Scipy]], or implement it yourself using what it does offers.

