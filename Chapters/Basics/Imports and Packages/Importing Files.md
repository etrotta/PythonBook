### Organizing and Reusing Code

So far all of our code has been stored in a single file, but that would get hard to work with as our programs grow larger.

In order to organize your code in larger projects, you'll want to split your code into different files and import functions from other files using the `import` statement.

```py
# geometry.py

def calculate_square_area(side: float) -> float:
	return side ** 2

# main.py
from geometry import calculate_square_area

side = 10
area = calculate_square_area(side)
print(f"The area of a square with {side=} is {area}")
```

### Subfolders and path resolution

%% TODO IMPROVE THIS AND ADD A LOT OF EXTERNAL RESOURCES %%
%% ALSO ADD A LINK TO A GITHUB TEMPLATE? %%

For the above example to work, you will need to create both files in the same directory and run `main.py`, but to organize things properly you'll want to use subfolders.

In order for Python to recognize your folders properly, you should add `__init__.py` files to each folder with files you want to run or import.
These files can be empty, or contain things you want to import directly from the folder

Example project structure (you would open `repository` as the Project Folder in your IDE)
```
repository/
├─ .git/
├─ src/
│  ├─ project_name/
│  │  ├─ helpers/
│  │  │  ├─ __init__.py
│  │  │  ├─ geometry.py
│  │  ├─ __init__.py
│  │  ├─ main.py
├─ pyproject.toml
├─ README.md
```

```py
# project_name/helpers/geometry.py
def calculate_area(side: float) -> float:
	return side * side
```
```py
# project_name/helpers/__init__.py
# Optional - The file could be empty as long as it exists, but adding this
# Allows for you to use `from project_name.helpers import ...`
from project_name.helpers.geometry import calculate_area

__all__ = [
	"calculate_area",
]
```
```py
# project_name/__init__.py
# Optional - The file could be empty as long as it exists, but adding this
# Allows for you to use `from project_name import ...`
# Style A
from project_name.helpers.geometry import calculate_area
# Style B (Requires project_name/helpers/__init__.py to import it)
from project_name.helpers import calculate_area

__all__ = [
	"calculate_area",
]
```
```py
# main.py

# Style A - Works even if both __init__.py are empty
from project_name.helpers.geometry import calculate_area
# Style B - Requires import in `project_name/helpers/__init__.py`
from project_name.helpers import calculate_area
# Style C - Requires import in `project_name/__init__.py`
from project_name import calculate_area

print(calculate_area(10))
```

When using this structure, you must always start your program by running the same file - in this case, `main.py`.
If you want to be able to run a file within a subfolder directly, you will need to add a `pyproject.toml` file and format your code as a package, using the structure explained in Further Reading.

### Further Reading

I strongly recommend formatting your code as installable packages and using `pip install -e` inside of a virtual environment.

To do this, you have to:
- Create a [[Extra/Ecosystem/Dependencies/Virtual Environments|Virtual Environment]]
- [Format your code as a package](https://packaging.python.org/en/latest/tutorials/packaging-projects/) (or a [namespace package](https://packaging.python.org/en/latest/guides/packaging-namespace-packages/))
	- Copy their project structure and follow up to the `Creating README.md` section, but ignore the parts about `Generating distribution archives` and `Uploading the distribution archives`
- Install it to your virtual environment, using `--editable` or `-e` as in `pip install -e .` so that it will stay synced as you make changes to your code.

### Exercises
Go back to previous exercises and split your code into multiple files
See if there is anything you can reuse between different exercises.
%% TODO make it more likely for there to be things to be used? %%

%% Maybe link something about Modules? `py -m whatever` %%

### Next Steps

