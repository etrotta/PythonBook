Unlike a traditional paper books, this Book is digital-first and lets you jump around back-and-forth thanks to hyperlinks, but this also means that the order in which you should read things can become confusing at times.
If you ever get lost, return to this page to get back on track.

You should start going through the Basic Chapters in order, and viewing the [[Chapters/Reference/Reference Index|Reference pages]] and solving Exercises as they are mentioned.

Overall, your experience should be:
```
-> Read a Main Chapter to understand the overall idea behind a concept
-> Briefly look at the linked Reference. Do not try to memorize all of it - just check back whenever you need
-> Practice playing around with some of the operations mentioned in the Reference and take your own notes

-> Read the linked Exercises and outline your plan to solve them, breaking it down into smaller steps
-> Think, take notes, sketch and experiment as you solidify your ideas and turn them into code
-> Go back and forth between the Exercise and the Reference to identify the operations you'll need and understand how to use them, further taking notes as you progress

-> Repeat until you finish the Exercise and write down what you have learned from solving it
-> (Optionally) Explore some of the Extra pages linked in that section, then go back to the Read Order
-> Proceed to the next Chapter and repeat
```

At any time, you can check the [[Extra/Extra Pages Index|Extra Pages]] or external resources (both those linked in the book, as well as searching for more on your own) for more information on specific Python features, issues you may come across, or extra information about other tools, though they may refer to concepts you have not learned yet.

> [!warning] This book quickly starts "branching" a lot
> Do not dive too deep into rabbit holes, and do not lose sight of what you are looking for. Understand the concepts, then return to focus on the core path.
> 
> The first time you read about each topic, focus on the Basic Chapters and the Exercises. Frequently consult the Reference Pages as you do the Exercises to look for relevant operations, and avoid Extras altogether. Do not worry about diving further at first, else you'll end up in an endless rabbit hole.
> 
> You should ignore "See Also" and "Further Reading" sections the first time you read through, but consider going back to (at least briefly) check them in the same order they were originally presented after you finish the Basic Chapters.
> They are mentioned across the book in case you need of them for your own projects, they are not requirements to progress through the Basic Chapters.


### Basic Chapters:
1. Setup
	1. [[Chapters/Basics/Introduction - Setup/About this book|About this book]]
	2. [[Chapters/Basics/Introduction - Setup/Installing Python|Installing Python]] and setting it up
	3. [[Chapters/Basics/Introduction - Setup/Hello World|Hello World]], running your first program
2. Variables and functions
	1. [[Chapters/Basics/Variables and Functions/Variables and Data Types|Variables and Data Types]], explaining the basic data types and the operations you can do with them
		- Exercise: [[Chapters/Excercises/String Operations 1|String Operations 1]]
		- Exercise: [[Chapters/Excercises/Numeric Operations 1|Numeric Operations 1]]
	2. [[Chapters/Basics/Variables and Functions/Functions|Functions]], letting you define custom operations by piecing together built in ones
		- Exercise: [[Chapters/Excercises/Numeric Operations 2|Numeric Operations 2]]
	3. [[Chapters/Basics/Variables and Functions/Types of Collections|Types of Collections]], letting you work not only with individual values, but with collections of them such as lists of numbers or mappings like `person name -> information about the person`.
		- Exercise: [[Chapters/Excercises/List Operations 1|List Operations 1]]
		- Exercise: [[Chapters/Excercises/Dictionary Operations 1|Dictionary Operations 1]]
		- Challenge: [[Chapters/Excercises/Set Operations 1|Set Operations 1]]
3.  Control Flow
	1. [[Chapters/Basics/Control Flow/Conditional Statements|Conditional Statements]] statements, using `if`, `else` and `elif` statements to control the flow of the program
		- Exercise: [[Chapters/Excercises/Dictionary Operations 2|Dictionary Operations 2]]
		- Challenge: [[Chapters/Excercises/User Input 1|User Input 1]]
	2. [[Chapters/Basics/Control Flow/Looping over data|Looping over data]], using `for` and `while` loops to execute repetitive operations for multiple items
		- Exercise: [[Chapters/Excercises/Numeric Operations 3|Numeric Operations 3]]
		- Exercise: [[Chapters/Excercises/Numeric Operations with Collections 1|Numeric Operations with Collections 1]]
4. Input and Output
	1. [[Chapters/Basics/Input and Output/Input and Print|Input and Print]], learning common patterns to handle data input and format your output
		- Exercise: [[Chapters/Excercises/User Input 2|User Input 2]]
	2. [[Chapters/Basics/Input and Output/Working with Files|Working with Files]], programmatically reading from and writing to files to parse data and save results
		- Exercise: [[Chapters/Excercises/Files 1|Files 1]]
5. Imports and Packages
	1. [[Chapters/Basics/Imports and Packages/Importing Files|Importing Files]], organizing your project across multiple files
		- No Exercises. Try updating some of your previous solutions to use it instead.
	2. Exploring [[Chapters/Basics/Imports and Packages/The Standard Library|The Standard Library]], taking a brief look at modules you can use to access more functions included with Python
		- Exercises (pick 2 or 3 depending on what you want to learn, not all of them): 
			- [[Chapters/Excercises/Libraries/Random 1|Random 1]], [[Chapters/Excercises/Libraries/Datetime 1|Datetime 1]], [[Chapters/Excercises/Libraries/Regex 1|Regex 1]], [[Chapters/Excercises/Libraries/Math 1|Math 1]], [[Chapters/Excercises/Libraries/SQLite 1|SQLite 1]]
	3. Installing [[Chapters/Basics/Imports and Packages/Third-Party Packages|Third-Party Packages]], using packages created by other developers

%% 
	- Further reading
		 - Extra: Testing, learning to create simple unit tests using `unittest` to make sure your code is working as expected
		- Extra: Create an exe using `hatchling`?
		- Extra: Command Line Interfaces using `sys` and `argparse` 
		- Extra: File Streams, look back at the `input()` and `print()` function to understanding what exactly they're doing
		- Extra: [[Extra/Python Operations/Working with JSON|Working with JSON]], giving a basic structure to data instead of just working with text files
		- Extra: Databases, working with actually structured data
		- Extra: Network requests, sending and receiving data across the internet
%%

### Project Start
After learning about the basic data types, functions, collections, conditional statements and loops, you should now be ready to start working on a project.

There is still a lot to learn, but with the foundations you've built so far, you can now choose a path to see things from an angle that is more relevant for you, and should be able to complete a medium sized project.

> [!note]- Major things you may still be missing
> After the foundations, the next biggest thing you should learn before working on real production-grade projects is by far Object Oriented Programming, but given its complexity, we are postponing it.
> Other than that, Error Handling is also of very high importance in real applications, but weighting the extra burden against the sense of accomplishment and motivation you should get from working on your own projects, we also postpone it a bit.

##### Projects Overview

You have the following projects available now:
- Data Science: Learn how to use industry standard tools used for data science, analyzing datasets and creating compelling visuals.
	- Tools used: numpy, pandas, plotly
	 %% ...definitely should still use pandas, but maybe also provide a polars version?%% 
- Web Backend: Create and host your own Website integrated with a database
	- Tools used: fastapi, gotta find a good async SQLite driver or ORM
- Discord Bot: Create and host your own Bot integrated with a database, TODO DETERMINE FEATURES
	- Tools used: discord.py, maybe some db???
- Pokedex CLI: Create a Command Line Tool that interacts with a Pokemon REST API in order to retrieve information
	- Tools used: httpx, pydantic, whatever was the FastAPI adjacent CLI library
- Open for more suggestions
- Just pls don't let there be a demand for chatbots
%% I ain't making a scraper nor desktop automation program no matter how much demand there is for one %%
%% CLI, GUI or games could be a reasonable demand, but I don't know shit about either of them %%

For further instructions, follow the Project Guide by clicking on the project you want to follow, and refer to for further instructions instead of this Read Order.
%% Things to add on all Project Guides

8. Setting up a series project: GitHub and Third-party Libraries
	1. Create a GitHub repository (note: probably better to provide templates for some, specially discord.py)
	2. Setup a [[Extra/Ecosystem/Dependencies/Virtual Environments|Virtual Environment]] and learn how to use `pip` to install popular Python packages, and learn the Hello World equivalent of `numpy` or `requests`
	2. 
10. Error Handling
	1. Catching errors, dealing with issues such as invalid input values for built in operations.
	2. Raising errors, checking if the inputs are valid for your custom operations.
	- Further Reading:
		- Extra: Breakpoints and debugging

 %%

%%
The projects above should be pretty much BASIC difficulty

Some thoughts on more projects
BASIC
rejected due to being an unpopular library:
- lancedb full text search
rejected because I don't feel like it's worth teaching about:
- web scraping
- desktop automation
- chatbots
- stable diffusion (...tbh maybe I'd write it if I had a GPU sadge)
rejected because I don't have enough domain specific knowledge to teach about it:
- graphical user interface
- (simple?) pygame-ce game

MEDIUM
consideration:
- machine learning (sklearn classification, pytorch using pretrained something)
	- maybe TTS/STT?
- ~~graph databases? idk probably not worth it but I like them...
	maybe at least mention Kuzu as an Extra~~
- Create a graph visualization replicating Obsidian's relationship graphs (parse .md files, find relations, create graph, viz graph, maybe store in Kuzu)
- analyzing your own Discord data?
- something with Riot Games API?
	- Legends of Runeterra???
- something with Hypixel API?....... oh god pls no
- something something PIL image editing
rejected cuz my skill issue:
- sudoku solver

ADVANCED
consideration:
- deep learning (creating your own model and training it from scratch)
- Real time BlueSky API Ingestion
- ActivityPub
rejected because I am not qualified to:
- your own programming language

%%