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

`import` does not import the functions or classes directly instead imports the module only. To access the functions inside the module the dot(`.`) operator is used.

- We can assign attributes from a module 

- We can import a module and rename it locally using `as`:
```Python
import my_module as renamed_module

renamed_module.my_function()
```

- We can import specific attributes from a module using `from`:
```Python
from my_module import my_function

my_function()
```
By importing specific objects from the module we don't need to use the `.` operator.

References to names in modules are [[Classes, objects and inheritance#^d39e86|attribute]] references: in the expression `modname.funcname`, `modname` is a module object and `funcname` is an attribute of it. In this case there happens to be a straightforward mapping between the module’s attributes and the global names defined in the module: they share the same [[Namespaces and Scope|namespace]].