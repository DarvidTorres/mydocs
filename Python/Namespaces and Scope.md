- A namespace is a mapping from names to objects. Most namespaces are currently implemented as Python [[dictionaries]], but that’s normally not noticeable in any way (except for performance), and it may change in the future.
	- A dictionary namespace maps the names (as keys) to their respective objects (as values).

There is no relation between names in different namespaces; for instance, two different modules may both define a [[Python/Functions/Functions|function]] `maximize` without confusion — users of the [[modules]] must prefix it with the module name.

Types of Namespaces:
- **Local Namespace**: Specific to a function or method; created when the function is called and lasts until the function returns.
- **Global Namespace**: Specific to the current module or script. This namespace is created when the module is loaded and lasts until the script ends or the module is unloaded.
- **Built-in Namespace**: Contains built-in functions and exceptions; created when the Python interpreter starts and exists as long as the interpreter runs.

- Name mangling in Python is a mechanism used primarily for name conflict resolution.