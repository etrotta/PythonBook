### Python's Superpower: The Ecosystem

The main reason why Python has became so popular is the packages ecosystem, with extremely powerful and %% relatively %% simple to use libraries.

Unlike the Standard Library, these may be created and shared by any user online, including both large companies and individual developers, and must be installed before you can import them.

Similarly to the standard library, they are used to import operations created by others, which could range anywhere from more efficient numerical operations to interacting with other programs via network requests.

### Before Installing

> [!warning]
> **Be careful when installing third-party packages:** Installing a package is as dangerous as installing an executable file and running it. Do not install packages from sources you cannot trust.

If you haven't yet, I strongly recommend creating a [[Extra/Ecosystem/Dependencies/Virtual Environments|Virtual Environment]] before running `pip install` so that you will not pollute your global installation. This is not any safer, but it can help avoid version conflicts.

### Installing packages

You can use `py -m pip install` to install packages to your active virtual environment, for example `py -m pip install requests` or `py -m pip install numpy polars plotly`

Using `pip install` directly might not work correctly if your environment variables aren't configured properly, but it should work if you have an active virtual environment.

### Troubleshooting
See [[Extra/Ecosystem/Dependencies/Multiple Python Versions|Multiple Python Versions]] and [[Extra/Ecosystem/Dependencies/Managing Dependencies|Managing Dependencies]] for some common problems and more detailed instructions.

### Common Packages

A non-extensive list of some third-party packages you may want to look into:
- Data Science:
	- [[Extra/Libraries/Data Science/Numpy|Numpy]], a popular library which provides efficient operations for working with numeric arrays
	- [[Extra/Libraries/Data Science/Pandas|Pandas]], a popular [[Extra/Libraries/Data Science/Data Frames|Data Frames]] library based on numpy
	- [[Extra/Libraries/Data Science/Polars|Polars]], a newer Data Frame library, faster and with better support for large datasets
	%% TODO add plotting? matplotlib / plotly? %%
	%% TODO deep learning? torch / transformers? %%
%% TODO ADD DATABASES? %%
- Network requests (client):
	- [[Extra/Libraries/Networking/Requests|Requests]], providing an extremely user friendly way to make network requests
	- [[Extra/Libraries/Networking/Httpx|Httpx]], with more advanced features and async support
- Web servers (backend):
	- [[Unorganized/MISSING|Django]]
	- [[Unorganized/MISSING|FastAPI]]
	- [[Extra/Libraries/Generic/Pydantic|Pydantic]], for data parsing and validation
	%% might have to think a bit about how much I want to explain WSGI/ASGI and alike, and if I want to mention servers themselves here or only within their pages %%
	%% honestly I am not even going to mention Flask nor Starlite %%
- Specific applications %% not sure if I really want to keep this or will just remove it later %%
	- [[Unorganized/MISSING|discord.py]] for Discord Bots
	- [[Unorganized/MISSING|telegram whatever it was]] for Telegram bots
	- [[Unorganized/MISSING|something something BlueSky?]]
%% Other things I might want to mention...
ruff
python-opencv
pillow
Jupyter?
SQLAlchemy
arrow
openpyxl?
some CLI library
pygame-ce
something for cryptography?
databases
- postgres (iirc psycopg3, asyncpg)
- mongodb (pymongo & motor)
- neo4j? kuzu?
- may as well mention lancedb

Maybe:
langchain and other LLM stuff


I do NOT want to mention:
selenium
bs4
youtube downloaders
whatsapp (user) bots
google wrappers that use web scraping (neither search nor translation)
cryptocurrency
stock market


%%
