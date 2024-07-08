### Exercise 1 - Hello, person
Use [[Chapters/Reference/Data Types/Strings|Strings]] and their operations to greet a person based on a `name` variable.
```py
name = "Mark"
print(...)
# Expected Output: "Hello, Mark!"
```

### Exercise 2 - Formatting tables
Use [[Chapters/Reference/Data Types/Strings#^c697af|String formatting specifiers]]  to align a table and control the number of decimal places displayed.

```py
# Modify only this line, in particular replace the `0` part:
ROW_FORMAT = "{name:0} | {age:0} | {score_perc:0}"

# Do not edit the part under this.
yuumi = {"name": "Yuumi", "age": 9, "score_perc": 0.01}
caitlyn = {"name": "Caitlyn", "age": 25, "score_perc": 0.5}
kled = {"name": "Lord Colonel Major Centurion Kled", "age": 1000, "score_perc": 0.13}

def main():
	print("Name                              |  Age | Score")
	print('------------------------------------------------')
	print(ROW_FORMAT.format(**yuumi))
	print(ROW_FORMAT.format(**caitlyn))
	print(ROW_FORMAT.format(**kled))

main()
```

> [!caution]- Solution
> `ROW_FORMAT = "{name:<33} | {age:>4} |  {score_perc:.2f}"`
