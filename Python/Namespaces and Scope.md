# Namespaces

- A namespace is a mapping from names to objects. Most namespaces are currently implemented as Python [[dictionaries]], but that’s normally not noticeable in any way (except for performance), and it may change in the future.
	- A dictionary namespace maps the names (as keys) to their respective objects (as values).

There is no relation between names in different namespaces; for instance, two different modules may both define a [[Python/Functions/Functions|function]] `maximize` without confusion — users of the [[modules]] must prefix it with the module name.

- Namespaces are created at different moments and have different lifetimes.
- The namespace containing the built-in names is created when the Python interpreter starts up, and is never deleted.
- The built-in namespace contains the names of all of Python’s built-in objects.
- **Built-in Namespace**: Contains built-in functions and exceptions; created when the Python interpreter starts and exists as long as the interpreter runs.

```Python
dir(__builtins__)
type(__builtins__)
```
Note: The `dir()` method in Python is a built-in [[Python/Functions/Functions|function]] used to list the [[Classes, objects and inheritance#^d39e86|attributes]] and methods of an [[Classes, objects and inheritance#Objects|object]]. If no parameters are given, `dir()` lists the names in the current local scope.

- **Global Namespace**: Specific to the current [[Modules|module]] or script. This namespace is created when the module is loaded and lasts until the script ends or the module is unloaded.
- **Local Namespace**: Specific to a [[Python/Functions/Functions|function]] or [[Methods|method]]; created when the function is called and lasts until the function returns.
- **Enclosing Namespace**: Enclosing namespaces occur in scenarios where you have a [[Python/Functions/Functions|function]] defined inside another function—a nested function.
# Scope

A _scope_ is a textual region of a Python program where a namespace is directly accessible. “Directly accessible” here means that an unqualified reference to a name attempts to find the name in the namespace.

- In Python, there are generally three levels of scope before the built-in scope:



- Name mangling in Python is a mechanism used primarily for name conflict resolution.