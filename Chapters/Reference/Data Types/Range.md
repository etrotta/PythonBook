The `range()` function allows for you to create a sequence of integers, and its `start, stop, step` arguments work similar to that of slicing.

You can call it in three different forms, by specifying a different number of arguments:
- One argument `range(stop)`, which sets `start=0` and `step=1`
- Two arguments `range(start, stop)`, which sets `step=1`
- Three arguments `range(start, stop, step)`

`range()` itself does not stores all numbers, it only materializes the collection when needed
(TODO link something like [[Unorganized/MISSING|Lazy vs Eager]]), so you must call `list()` or iterate over it to see each value within the range

- `list(range(10)) == [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]`
- `list(range(5, 10)) == [5, 6, 7, 8, 9]`
- `list(range(0, 10, 2)) == [0, 2, 4, 6, 8]`


The arguments you pass to `range()` as well as the values it gives you must all be integers. Some libraries like numpy offer similar functions that accept floats, such as `np.arange`.
