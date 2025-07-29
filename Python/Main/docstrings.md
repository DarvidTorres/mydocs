Python docstrings are the string literals that appear right after the definition of a function, method, class, or module.
- For triple-quoted strings, always use double quote characters to be consistent with the docstring convention in [PEP 257](https://peps.python.org/pep-0257/)
- The line length should be limited to 72 characters.

## function docstrings

The docstring for a function or method should summarize its behavior and document its arguments, return value(s), side effects, exceptions raised, and restrictions on when it can be called (all if applicable). Optional arguments should be indicated. It should be documented whether keyword arguments are part of the interface.

## class docstrings

The docstring for a class should summarize its behavior and list the public methods and instance variables. If the class is intended to be subclassed, and has an additional interface for subclasses, this interface should be listed separately (in the docstring). The class constructor should be documented in the docstring for its `__init__` method. Individual methods should be documented by their own docstring.