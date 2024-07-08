# Things to pay attention to before installing a dependency
Whenever you are using a [[Extra/Ecosystem/Dependencies/Virtual Environments|Virtual Environments]] to prevent version conflicts or not, here are some things to keep in mind when installing dependencies:

### Make sure it is safe
Installing Python Packages can be dangerous. `pip install example` is as dangerous as going to example.com, finding the first exe you can find and running it. Do not install packages from sources you do not trust - even if you do not import them, they can run arbitrary python code during installation.

### Do you really need of it?
Avoid installing packages if you can trivially implement what you need them for yourself. External dependencies can be a pain between breaking changes, restricting your supported versions, and the possibility of them not being maintained.

That said, there are many cases in which it may make sense for your project. Below are 
- some examples of cases in which nearly all projects related to a given area should be using external dependencies
- some examples of cases in which it might make sense, but you may want to consider not using a dependency
- some examples of cases in which you should definitely not use third party dependencies for

##### Things you should install packages for
 - Data Science (`numpy`, `scipy`, `pandas`, `polars`, `pytorch`, `tensorflow`, ...) - Numerical computing, efficient transformations over large datasets, machine learning and such are cases in which implementing things yourself would not only be hard but extremely slow. These packages are usually written in faster languages such as C or Rust, and are the reason why despite being a relatively slow programming language, Python is so popular in Data Science, Machine Learning and Artificial Intelligence
 - Images, videos, plotting (`PIL`, `moviepy`, `plotly`, `matplotlib`) - Similar to the above, a lot of work and you want to be as fast as possible.
 - Database connectors - Usually you should prefer using such packages when available, specially if they are officially created by the developer behind the product you are connecting to. May be a lot of work, and there are also some security concerns such as safely passing parameters to prevent SQL Injection.
 - Network requests (`requests`, `httpx`, `aiohttp`) - A lot of work and a lot more complicated than you would imagine. In some cases, may also involve security concerns.
- Anything related to security, hashing, encrypting, cryptography - **Never** implement this sort of things yourself if you can avoid it. Not only is it hard to implement it correctly, the smallest bug can go unnoticed and lead to disastrous security vulnerabilities.
- Web servers (`fastapi`, `django`, `flask`) and in some cases bots (`discord.py`, `python-telegram-bot`) - Web servers and alike require a lot of work, so it's much better to use popularly used, industry-standard tools than implementing things yourself.
- Game engines (`pygame-ce`, `ursina`) and UI Frameworks - That category of tools take care of the boring and complex parts of making things work, and let you focus on the logic of your game or project.

These are just some examples, both as far as the areas go, as well as far as the libraries within these areas go. There are hundreds of other areas that make perfect sense to install dependencies for and new libraries being created every day, and I cannot possibly list all of them, but hopefully this should give you an idea of how important they must be to justify installing one.

##### Things you may or may not want to install a package for
- REST APIs: Sometimes there are wrappers around REST APIs, but at times they may be missing features or be unmaintained, or you might not even find one for the API you are using at all. In these cases, you should just use a more generic library such as `httpx` and interact with it through network requests directly.

##### Things you should definitely not install a package for
- Basic functionalities such as string formatting: Python already provides a lot of tools for many common tasks between the built-in classes and the standard library. Nobody wants to see another history like [JavaScript's left-pad](https://www.theverge.com/2016/3/24/11300840/how-an-irate-developer-briefly-broke-javascript).
- Outdated / Unsupported tools: If a package no longer supports modern python versions (at least [versions under Security Support](https://endoflife.date/python), but preferably even Active Support versions), you should avoid using such outdated packages as much as possible. In particular, **absolutely never** use Python 2.
- Forcefully bringing features from other languages into Python or intentionally cursed libraries: Oftentimes such libraries will fail to make use of Python's strengths, be incompatible with other tools, or completely break in unexpected ways.
Python may not support everything you ever wanted, but it already has a lot of features included in the standard library. You might have to adjust your way of thinking to make best use of the tool you are currently using instead of wishing it behaved like a different tool.

# Actual Commands - pip

### Installing packages
Now that you have a good idea of the dangers of installing packages, and whenever you should even be installing them in first place, let's see how to actually install them:

- (Optional) Create a [[Extra/Ecosystem/Dependencies/Virtual Environments|Virtual Environments]] first
- Find the package you want to install, preferably through popular tutorials or guides.
- - Even another warning: Code generated by LLMs such as ChatGPT or Gemini may include packages which do not exist, do not work, or originally did not exist but then were claimed by a malicious actor and now contain malware. Be extra careful when installing dependencies generated by tools that can hallucinate.
- Actually install it: Use `py -m pip install example` to make sure it is installed to the right interpreter, or just use `pip install example` if you are already inside of a virtual environment.

### Managing Packages
You should manually keep a list of your direct dependencies (those which you explicitly install, as opposed to the dependencies indirectly required by those you installed yourself), either in a text file or inside of `pyproject.toml`, but you can also create a `requirements.txt` file containing all of your current dependencies in order to (re)install them in a different environment, be it a venv or a completely different machine.

> [!tip]
> You can use `pip --help` in a terminal to get a list of the commands alongside their descriptions, or `pip command --help` to get more information about a particular command and its options.

- install a package: `pip install example`. Again, please remember all the security concerns mentioned above.
- list packages: `pip list`
- uninstall a package: `pip uninstall example`
- "freeze" into a `requirements.txt` file to install it in another environment: `pip freeze > requirements.txt`
- install from a file created by the above command `pip install -r requirements.txt`

Side note:
- the `> file.txt` part in `pip freeze > requirements.txt` is not special to `pip`, it is just a way of directing the output of any command to a file instead of the standard output (displaying in the terminal)
- the `-r file.txt` part in `pip install -r requirements.txt` is an argument to `pip install`, and it is up to `pip` to interpret that it means it should read a file with that name, but the file does not necessarily have to be called `requirements.txt`

### Common Issues
If you are still seeing a `ModuleNotFoundError` after installing a dependency, here are some things to check:
- Read the entire error and check the library description on its https://pypi.org page
- Did it install successfully?
- - If you are using an outdated library or a recently released Python version, the library might not support the Python version you are using
- - Did you pin it to an old version? Similarly to the above, if you are using a requirements.txt file that pins it to an old version, it may not work in your Python version
- - Some libraries might require for you to manually install compilers for other languages first, if they are partially written in different languages.
- - Some libraries will only work for certain Operating Systems
- Are you using the correct `import` statement? Some libraries may use different names for the `pip install` command and the actual `import`, a common example being `pip install pillow` vs `import PIL`
- Did you install to the same environment that you are using to run the code? See [[Extra/Ecosystem/Dependencies/Multiple Python Versions|Multiple Python Versions]]