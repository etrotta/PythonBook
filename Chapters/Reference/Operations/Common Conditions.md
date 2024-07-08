### Conceptually

Checking conditions is the essence of `if` statements. In this page, we cover some common patterns of conditions you may need to check.

##### Checking values

The simplest and amongst the most common operations, 
```py
if number > 3:
	...

if number == 5:
	...

if string.lower() == "hello world":
	...

if string in ("bulbasaur", "charmander", "squirtle"):
	...
```

You can use `==` to check equality, `<` and `>` and other [[Chapters/Reference/Operations/Logical Operations|Logical Operations]], as well as other operations applicable to the types you are working with, for example all collections support the `in` expression in some way.

##### True-ish and False-ish values

Remembering some aspects of numbers and collections:
- `0` is treated as `False`, all other numbers are treated as `True`
- empty collections such as `''`, `[]` or `{}` are treated as `False`, any collections containing values are treated as `True`

Some overall tips:
- instead of checking things like `if len(list) > 0` you can just do `if list:`
	- similarly for things like `if len(list) == 0:`, you can do `if not list:`
- most of the time,  `== True` is redundant
- most of the time, you should use `not value` over `== False`
	- there are also `a is not b` and `a not in b` variations for `a is b` and `a in b` operators

##### None

[[Chapters/Reference/Data Types/Special Values#^3bff32|None]] is oftentimes used as a default value for function parameters, and when doing so you'll typically need to check if it's been given a value or not.

`None` is also treated as False-ish, so if you want for it to have the same behavior as `False`, `0`, `[]` and other False-ish values, you can just do `if value:`

```py
def function(value: int | None = None):
	if value is None:
		value = 42
	return value
```
%% Maybe mention `|` being Type Union? %%

##### Identity vs Equality
If you want to treat `None`, `True` or `False` singletons differently from other True-ish or False-ish values, you should use `if value is None:` (or `is True`, `is False`) instead of `if value == None:` to compare based its [[Extra/Abstract Concepts/Object Identity|Object Identity]].

Never use `is` for numbers or strings, just `==`. You shouldn't ever need to check identity for integers/strings, and it may work in unexpected ways.
For lists or dictionaries, you could use it to check if it's exactly the same object (as opposed to another collection with the same data, like a copy), but it is very unusual for you to want to check that.

For example, if you check `True == 1`, `False == 0` or `[] == []`, they are true, but not `True is 1`, `False is 0` nor `[] is []`.
When it comes to `None`, that is less of an issue, but it can lead to some problems working with third-party libraries that modify the behavior of `==`, such as [[Extra/Libraries/Data Science/Numpy|Numpy]] arrays broadcasting.

> [!note]- Detailed numpy example
> If you check `[1, 2, 3] == None`, with a normal list Python will just return `False` just like it would for `is None`.
> 
> However, when you perform a `==` operations on arrays, numpy may broadcast it, comparing the value against _each_ element and returning a new array.
> For example, `array([1, 2, 3]) == 2` would return `array([False, True, False]))`
>
> As such, if you check `array([1, 2, 3]) == None` it'll return `array([False, False, False]))` instead of just a normal `False`.
> This would lead to unexpected behavior checking `if array == None:`, and numpy even gives you an error for it.

### See Also

[[Chapters/Reference/Operations/Pattern Matching|Pattern Matching]]