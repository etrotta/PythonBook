### Integers
Integers are natural or negative numbers without decimal places, such as `0, 1, 2, 3, -1, -2, -3`. Integer literals are created by just entering the value directly.

> [!tip]- Tip: Hexadecimal/Binary literals and Visually separating decimal places
> You can prefix numbers with `0x` to write numbers in hexadecimal form, such as `0xffffff`, `0o` for octal, and `0b` for binary such as `0b101010`.
> You can also use `_` within numbers just to make it easier to visualize them, e.g. `123_456_789`, `10_000_000_000` or `0b0010_1010`.
> Decimal numbers cannot be prefixed with leading `0`s, but you can include them in other bases

### Floats
Floats (Floating Point Numbers) are rational numbers with decimal places, such as `0.0`, `-1.0`, `3.14`, `1e-100` or `1.41`.
It is important to note that computers can only work with data they can represent, as such, there is no way to work with Irrational numbers.

 > [!tip]- Tip: Precision Issues
> Since computers are working with base-2 binary numbers under the hood, as opposed to using a base-10 system like humans, you may see unexpected results even on simple operations such as `0.1 + 0.2` returning `0.30000000000000004` instead of just `0.3`. [Further reading if you want to understand why that happens](https://0.30000000000000004.com/), but know that issues are exacerbated with extremely large or extremely small numbers.
> If you need of perfect precision, use Integers or look into the [[Extra/Libraries/Standard Library/Modules/Decimal and Fraction|Decimal and Fraction]] libraries instead. Precision issues are not present when working with them as Python uses as much space as it needs to represent them perfectly.

You can use scientific notation (`e`) as part of the number literal to create floating point numbers such as `1e100` or `1e-100`. Trying to create a float that cannot be represented such as `1e500` will give you a [[Chapters/Reference/Data Types/Special Values#^284102|special]] `inf` value.

### Complex (Imaginary) numbers
We will not go into detail about them in this book, but Complex numbers are a pair of a real number with an imaginary number. They share the same limitations as floats.
You can use `j` as part of a number literal to create a complex number with an imaginary part, and use `real_number + complex_number` to create a complex with both a real and a complex part. For example, `print(1j)` or `print(4 - 3j)`.

You may want to use the `cmath` module of the standard library if you need to perform operations on complex numbers.

### Booleans
Booleans refer to `True` or `False`. These are the only two possible values a Boolean variable can take.
It may sound weird to say that `True` and `False` are numbers, but that has its roots in older programming languages that lacked a Boolean type, and is still used today since it's useful in some cases.

When used as a number, `True` will act the same as the integer `1`, and `False` will act as the integer `0`. To create a Boolean literal, just write `True` or `False` in code without quotes.

## Supported Operations
- [[Chapters/Reference/Operations/Numeric Operations|Numeric Operations]]
- [[Chapters/Reference/Operations/Logical Operations|Logical Operations]]

## Further Reading
The standard library contains [[Extra/Libraries/Standard Library/Modules/Decimal and Fraction|Decimal and Fraction]] types, for when you need of perfect precision while working with real numbers.
