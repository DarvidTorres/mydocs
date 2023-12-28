- IPython adds on top of the normal Python syntax, *magic* commands.
- *magic* commands can be:
	- *line magics*, denoted by `%` and operate on a single line of input.
	- *cell magics*, denoted by `%%` which operate on multiple lines of input.

Example: Create a `mymodule.py` file with the following Python code:
```Python
def mymodule():
    """Print message"""
    return print("Module file")
```

Then run the following in IPython:
```IPython
%run myscript.py
mymodule()
```
