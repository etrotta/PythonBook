
If you want to install multiple different Python versions, you can just install the downloader for each of them from https://python.org and setup each of them - it should install each version separately into its own folder without issues, but there is a chance things will break if you do not specify which version to use later.

### Dependencies not being found

Sometimes you might end up with issues such as getting a `ModuleNotFoundError` even though you just `pip install`'ed it.

The most common cause of that is having multiple different Python versions installed locally, and the Python version you are using to run your code being different from the one you installed it to.

You can use the following commands to check which versions you have, and where they are installed to: 
```
py --list

pip --version
py -m pip --version
python -m pip --version
```
Pay attention not just to the Python and pip versions, but the path of the folder they are installed in.

To solve this, you could use `py -3.VERSION -m pip` and `py -3.VERSION file.py` to make sure you are using the correct version, but I would recommend using [[Extra/Ecosystem/Dependencies/Virtual Environments|Virtual Environments]] instead, which will automatically select the correct version both when installing packages as well as when running your code as long as you have them activated, besides having other benefits.

See also:
- [[Extra/Ecosystem/Dependencies/Virtual Environments|Virtual Environments]]
- [[Extra/Ecosystem/Dependencies/Managing Dependencies|Managing Dependencies]]
