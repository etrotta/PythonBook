> [!warning] This page is optional, and mentions some advanced concepts

### Conceptually

When manually opening and closing connections to external resources, there are a lot of things that could go wrong and cause the resources not to be released properly. This applies not only to files, but also to databases, network connections and some other services.

Traditionally you would use `try: finally:` statements such as

```py
try:
	file = open(...)
	# do something with file
finally:
	file.close()
```

But as that's rather verbose, Python provides an interface called context managers that take care of opening and closing such resources for you

```py
with open(...) as file:
	# do operations with file
```

This pattern is commonly adopted by most libraries that can benefit from it, so overall you should prefer to use it over other methods when available, including the built-in `open()` method.

It's also useful for some other operations, setting configurations only to specific parts of your program, be it library-specific printing options or mocking functions as part of test suites.

### Creating your own

%% I probably should move it to an Extra page %%
> [!error] This is a lot more advanced than the Main Chapter this page is referenced in

Context managers use the `__enter__` and `__exit__` magic methods to define what to do when it enters and exits the context.

The easiest way to create one is using the `contextlib` standard library module, but you can also create your own classes implementing them.

```py
import contextlib
import pathlib

folder = pathlib.Path("/example")

@contextlib.contextmanager
def get_file(name: str, *args, **kwargs):
	path = folder / name
	try:
		file = path.open(*args, **kwargs)
		yield file
	finally:
		file.close()

with get_file('test.txt', 'r') as file:
	print(file.read())
```


```py
configuration = {"max_rows": 10, "max_columns": 10}

class Config:
	def __init__(self, **options):
		self.options = options
		self._restore = {}

	def __enter__(self):
		overwrites = self.options.keys() & configuration.keys()
		self._restore = {k: configuration[k] for k in overwrites}
		configuration.update(self.options)
	
	def __exit__(self, exc_type, exc_val, exc_tb):
		# the 'exc' variables can be used when an error happens inside of the context manager
		configuration.update(self._restore)

print(configuration)  # 10, 10
with Config(max_rows=None):
	print(configuration)  # None, 10
	with Config(max_columns=2):
		print(configuration)  # None, 2

print(configuration)  # 10, 10
```

### Further Reading

https://docs.python.org/3/reference/datamodel.html#with-statement-context-managers
https://docs.python.org/3/library/stdtypes.html#typecontextmanager
https://docs.python.org/3/library/contextlib.html