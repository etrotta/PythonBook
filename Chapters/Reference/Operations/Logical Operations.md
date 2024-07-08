### Conceptually
Logical operations let you compare values, such as checking if two numeric variables are the same, or later on determining what to do based on the user's input.
They are also used for operations such as sorting values.

### Logical operations:
- Equality: `x == y`, returns `True` or `False` Booleans based on whenever they are the same
- Greater than: `x > y`
- Lesser than: `x < y`
- Greater than or equal to: `x >= y` (Note: This is two characters, `>` followed by `=`, but some fonts may display it as a single `≥` character thanks to a feature called ligatures)
- Lesser than or equal to: `x <= y` (Note: same as above, just `<` instead of `>`)
- `is` / `is not`: Compares the [[Extra/Abstract Concepts/Object Identity|Identity]] of two objects. In practice you should only use it for `None`, or if you want literally `True` / `False`.

### Boolean operations:

^boolops

- Checking that two bools are True: `x and y`
- Checking that at least one of two bools is True: `x or y`
- Checking that at a bool is False: `not x` 

### Observations

In Python, you can chain some logical operations such as `1 < x < 3` or `False == False == False` and they will be executed as `(1 < x) and (x < 3)` or `(False == False) == (False == False)`, but in other languages that may execute them separately such as `(1 < x) < 3` = `boolean < 3`, so be careful if you move to another language later.

### Further Reading

##### Converting other types to to Booleans
When casting other values to Booleans using `bool()`, it'll use the following logic:
- `0` is treated as False, all other numbers are True
- empty collections are False, all other numbers are true
- `None` is treated as False

##### Performing Boolean operations on other types

If you perform operations such as `0 and 1`, `2 or 3`, `2 and 3`, `None or 5`, Python will covert the values to Booleans using the same logic as `bool()` to determine which of them to choose, then return the original values.

And Boolean operations will behave as:
- `x or y` will use the value of `x` if it's True-ish, otherwise it will use the value of `y`.
- `x and y` will use the value of `x` if it's False-ish, otherwise it will use the value of `y`
