When you install third party packages in Python, they get saved to a folder managed by Python, which by default is global and shared across multiple files and projects.

This is usually fine, but it can lead to problems if you need to use different versions of the same library for different projects, be it directly or indirectly because of your dependencies.

To solve this, you can create Virtual Environments for each of your projects, which let you tell Python to install your dependencies to a different folder, thus letting you isolate each project's dependencies.

Most Integrated Development Environments (IDEs) will include commands to create them for you such as `Python: Create Environment`, and let you select which one to use with commands such as `Python: Select Interpreter`. When using such commands, you might need to create a new Terminal before running any commands in it. 
Alternatively, you can do it manually with the following commands.

```
py -m venv .venv
./.venv/scripts/activate
```
To test that it worked, you may want to check `py -m pip --version` and `pip --version`.

### Related topics
[[Extra/Ecosystem/Dependencies/Multiple Python Versions]]
[[Extra/Ecosystem/Dependencies/Managing Dependencies|Managing Dependencies]]