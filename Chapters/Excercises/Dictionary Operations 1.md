### Exercise 1 - Manipulating dictionaries

Print Mark's number, then add a number of your choice for `"Luna"` and remove `"John"`'s number
```py
# numbers: dict[str, str], mapping name -> contact number

contacts = {
	"John": "+00 1111-1111",
	"Mark": "+00 9999-9999",
}
```

### Exercise 2: Basic Transformations

Transform the data from the format used in Exercise 1 into the following format:

```py
# persons: list[dict[str, str]], a collection of (field -> field information) mappings.

persons = [
	{"name": "Mark", "number": "+42 9999-9999"},
	{"name": "Luna", "number": ...},
]
```

> [!note]+ Note - You would need to use loops to do it automatically for all persons
> For now, create a function that returns a new dictionary given the `numbers` dictionary and a person's `name`, then manually run it for each person and create a list with these results.
