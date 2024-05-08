Conventions:
- `_my_var` (single underscore at the beginning): Indicate "internal use" or "private" objects. Objects named this way will not get imported by a statement such as: `from module import *`
- `__my_var` (double underscore at the beginning): Used to "mangle" class attributes -useful in inheritance chains.
- `___my_var__` (double underscore at the beginning and at the end): Used for system-defined names that have a special meaning to the interpreter.