### Getting information In and Out of programs

We have been using `print` to output information since the first page, and briefly used `input` to receive information from the user previously, but we haven't really looked into either of them in detail.

While programs can operate without any inputs or outputs, it they would be fairly useless without an output, so you'll usually want to either display the values to the user using `print()`, write to a file or send data to a different program.

Similarly, while programs can operate without inputs, that would mean they always have the same output every time, so you'll typically want to receive inputs in some form, be it asking from the user through the `input()` function, reading it from a file, or receiving it from other programs.

### Output: Printing

So far we've only used `print(thing)`, but you can specify multiple arguments for the print function, including [[Extra/Abstract Concepts/Advanced Functions|Variadic and Keyword arguments]]

```
>>> help(print)
Help on built-in function print in module builtins:

print(*args, sep=' ', end='\n', file=None, flush=False)
    Prints the values to a stream, or to sys.stdout by default.

    sep
      string inserted between values, default a space.
    end
      string appended after the last value, default a newline.
    file
      a file-like object (stream); defaults to the current sys.stdout.
    flush
      whether to forcibly flush the stream.
```

If you pass multiple arguments, it'll convert each of them to strings, then join with the `sep` (an ` ` space by default)
By default, it'll append a `\n` newline character at the end of the string, but you can overwrite it by specifying a value for the `end=` parameter such as `end='---'` or `end=''`.

Some examples:
```py
print(1, 2, 3, 4, 5, sep=', ')
print(1, 2, 3, 4, 5, sep='\n')

print(1, end=' ')
print(2)
print(3, end='')
print(4)
```

The `file` and `flush` parameters will be explained later, but in a nutshell, it allows for you to write to files and force the file stream to update (as opposed to buffering) whatever it may be connected to immediately.

### Input

You can use the `input()` function for getting user input through the terminal. It is simpler than print, only supporting one optional prompt and no other options

```
>>> help(input)
Help on built-in function input in module builtins:

input(prompt='', /)
    Read a string from standard input.  The trailing newline is stripped.

    The prompt string, if given, is printed to standard output without a
    trailing newline before reading input.

    If the user hits EOF (*nix: Ctrl-D, Windows: Ctrl-Z+Return), raise EOFError.
    On *nix systems, readline is used if available.
```

The user must press `Enter` to send the input to the program.
If you want to read one character at a time, you'll need to use a third-party library.
If you want to read multiple lines at a time, you could use a loop.
%% 
TODO Maybe add a link to one such library?
I don't even know any I'd recommend though tbh
btw if you're trying to use it with asyncio: It is blocking and you cannot do it asynchronously - iirc threading can work but I'm not sure, I barely ever use input() myself
%%

### Exercises

[[Chapters/Excercises/User Input 2|User Input 2]]

### Next Steps

Follow on to [[Chapters/Basics/Input and Output/Working with Files|Working with Files]] in order to save information to files, and read back from it

### Further Reading

Feel free to take a look at https://docs.python.org/3/library/sys.html#sys.stdin if you want to understand how input and print use file streams

