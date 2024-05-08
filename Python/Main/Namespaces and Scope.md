# Namespaces

- A namespace is a mapping from names to objects. Most namespaces are currently implemented as Python [[Dictionaries]], but that’s normally not noticeable in any way (except for performance), and it may change in the future.
	- A dictionary namespace maps the names (as keys) to their respective objects (as values).

There is no relation between names in different namespaces; for instance, two different modules may both define a [[Python/Functions/Functions|function]] `maximize` without confusion — users of the [[Modules]] must prefix it with the module name.

- Namespaces are created at different moments and have different lifetimes.
- The namespace containing the built-in names is created when the Python interpreter starts up, and is never deleted.
- The built-in namespace contains the names of all of Python’s built-in objects.
- **Built-in Namespace**: Contains built-in functions and exceptions; created when the Python interpreter starts and exists as long as the interpreter runs.

```Python
dir(__builtins__)
type(__builtins__)
```
Note: The `dir()` method in Python is a built-in [[Python/Functions/Functions|function]] used to list the [[Classes and objects#^d39e86|attributes]] and methods of an [[Classes and objects#Objects|object]]. If no parameters are given, `dir()` lists the names in the current local scope.

- **Global Namespace**: Specific to the current [[Modules|module]] or script. This namespace is created when the module is loaded and lasts until the script ends or the module is unloaded.
- **Local Namespace**: Specific to a [[Python/Functions/Functions|function]] or [[Methods|method]]; created when the function is called and lasts until the function returns.
- **Enclosing Namespace**: Enclosing namespaces occur in scenarios where you have a [[Python/Functions/Functions|function]] defined inside another function—a nested function.
# Scope

A _scope_ is a textual region of a Python program where a namespace is directly accessible. “Directly accessible” here means that an unqualified reference to a name attempts to find the name in the namespace.

- Name mangling in Python is a mechanism used primarily for name conflict resolution.

The scope of a name is the region of a program in which that name has meaning. The interpreter determines this at runtime based on where the name definition occurs and where in the code the name is referenced.

The interpreter searches for a name from the inside out, looking in the **l**ocal, **e**nclosing, **g**lobal, and finally the **b**uilt-in scope:

1. **Local:** If you refer to x inside a function, then the interpreter first searches for it in the innermost scope that’s local to that function.
2. **Enclosing:** If x isn’t in the local scope but appears in a function that resides inside another function, then the interpreter searches in the enclosing function’s scope.
3. **Global**: If neither of the above searches is fruitful, then the interpreter looks in the global scope next.

```mermaid

```


