### Exercise: Queue

Create a command line program to keep track of a queue, allowing for the user to add records to a list or pop the oldest.

The user should be greeted with the following message:
```
> py main.py
Running Queue Manager
Use "add ITEM" to add items to the queue
Use "pop" to remove items from the queue
Use "exit" to exit the program
Enter a command: 
```

Then be able to interact as
```
Enter a command: add Red
Added Red to the queue in position 0
Enter a command: add Green
Added Green to the queue in position 1
Enter a command: pop
Next element in the queue: Red
Enter a command: add Blue
Added Blue to the queue in position 1
Enter a command: pop
Next element in the queue: Green
Enter a command: pop
Next element in the queue: Blue
Enter a command: exit

(no output, program exits)
```

Anything ambiguous or otherwise unclear is left for you to decide how to handle, as long as it follows the example output.

As long as it works, you can do things differently from the way suggested by the Tips.

>[!tip]- Tip: Overall structure
> Create a collection to store the queue data.
> Create functions for each operation (adding or removing elements)
> Use a loop to continue running until the user asks to exit
> Ask for input at the start of each iteration
> Check for conditions to determine which function to run

> [!warning]- Tip: What to use for each part
> Use a list for the queue itself
> Use a `while` loop to continuously ask for input
> Use a string operations and conditional statements to check if the user wants to add to the queue or remove from it
> When adding, use string operations to separate the command itself from the name being added to the queue, and use list operations to get the position of the inserted item

### Optional Extra Challenge: Further improvement

Some ideas you can try to implement after clearing the main Exercise
- Add and remove multiple items with a single command
- Add Priority: When inserting, also ask for which priority to give to this element. When popping from the queue, first filter based on the priority before comparing based on the insertion order.
- Persisting data: Save to a file or database
	- Commands to Export to and Import from a csv file
	- Automatically sync to a [[Extra/Libraries/Databases/SQLite|SQLite]] database when adding or removing records
- Add multiple fields and format the data when removing elements from the queue

If you try to implement some of these suggestions, you may need to check Main Pages beyond the one that links to the Exercise, or even Extra pages and external resources.
