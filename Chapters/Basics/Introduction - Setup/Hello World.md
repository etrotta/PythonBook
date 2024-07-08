In order to make sure your Python installation is working properly, as well as per tradition, you should launch Python and make sure it is working properly.

### Running in the Terminal
Inside of any terminal (such as VSCode's integrated terminal, PowerShell or cmd.exe), run `py` to start the Python Interpreter.
On Windows, you can press `Win+R -> type "cmd" -> Enter` to launch a cmd.exe terminal, or even `Win+R -> type "py" -> Enter` to launch the Python interpreter directly.

Once inside of it, you should see a `>>> ` prefixing whatever you're typing. You can run Python code inside of it and it will execute line-per-line as you enter it. Run the following line:
```py
print("Hello world!")
```
If everything worked properly, you should see `Hello world!` greeting you back 
```py
>>> print("Hello world!")
Hello world!
>>>
```

> [!warning]
> Your terminal will be stuck inside of the Python interpreter until you exit, using the `exit()` function or `Ctrl+Z`. This means that if you try to use command line tools such as `echo` or `pip` they will fail as it is Python who is receiving them, not the terminal.

Make sure you are using straight quotes `"..."` or `'...'`, not curly quotes such as `“...”` or `‘...’`

### Saving to a file and running it from a terminal
You can also save your code to files and run it.
Open notepad normally or using `notepad file.py`,  then copy/paste your code into the file and save it.

> [!info]+ File extensions
> Make sure that it is saved as a `.py` file, not `.txt` or `.py.txt`. If you haven't yet, you may want to modify the "Show File Extensions" setting under your computer System Settings to always show them.

You can then run your file using `py file.py`, and it should display the output right under in the same terminal.
When running files like this, `file.py` may be either the relative path **from the current working directory** or the absolute file path between "" quotes.

If you are ever confused about what is your current working directory, you can open the File Explorer in it by typing `explorer .` into your terminal 

### Creating a file inside of VS Code and running with it
Most of the time, you should be working inside of an Integrated Development Environment (IDE) instead of using tools like notepad or cmd.exe to edit and run files manually.

First you will want to create an empty folder for your project, then open it from VSCode.
Make sure you have the official `Python` extension installed before proceeding.

> [!tip]- Extra steps on real projects
> For real projects, oftentimes you'll want to use a Version Control System (VCS) such as `git`, which would require initializing a new git repository at this step or creating a new GitHub repository from a template on the GitHub website then cloning it instead of creating an empty folder.
> In addition to version control, real projects will more often than not want to use [[Extra/Ecosystem/Dependencies/Virtual Environments|Virtual Environments]] to isolate and keep track of their dependencies.

Once you have your Project open inside of VS Code, you'll want to create a new file, paste your code, then save it as a `.py` file.
After saving your file, press `F5` to Run and debug the file you are editing, and it should display the output in the Integrated Terminal.

You can also use `Shift + Enter` to execute run your code one line at a time in the terminal.

### Next Steps

Head over to [[Chapters/Basics/Variables and Functions/Variables and Data Types|Variables and Data Types]] to learn about which forms of data are available inside of Python, and do basic operations involving them.

### Further Reading

You might want to check the [VS Code documentation](https://code.visualstudio.com/docs/languages/python), check the available commands on the Command Palette (`Ctrl + Shift + P`), look for more Extensions relevant to specific projects, or customize your hotkeys.

Once you start working on more complex problems, things will rarely work as you expect the first time, and you'll need to investigate where things are going wrong in your program.
You can always add print() statements in the middle of your code, but after a certain point, you'll want to learn how to use a [[Extra/Ecosystem/Tooling/Using the Debugger|Debugger]] to pause your code at any given point and investigate the state of the program.
