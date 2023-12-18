- A Python module is a file containing Python definitions and statements.
- A module can define functions, classes, and variables.
- A module can also include runnable code.
- To create a module save the code you want in a file with the file extension `.py`.

Save the file `my_module.py`
```Python
def my_function():
    """Print Hello World message"""
    print("Hello World")
```

Use the module we just created, by using the `import` statement:

```Python
import my_module

my_module.my_function()
```
Note: When using a function from a module, use the syntax: `<module_name>.<function_name>`, like in the example above.

