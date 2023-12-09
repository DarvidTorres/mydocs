- A function is a block of code which only runs when it is called.
	- The only operation on a function object is to call it: `func(argument-list)`.
- A function can return data as a result.
- Function objects are created by function definition.

syntax:
```Python
def <function_identifier>([parameter(s)])
	["""<docstring>"""]
	<suite>
	[return]
```
- The keyword `def` introduces a function definition.
- Follow the naming convention `lowercase_with_underscores` for function identifiers.
- You can pass data, known as parameters, into a function.
	- A **parameter** is a variable in a function definition.
		- It is a placeholder and hence does not have a concrete value.
	- An **argument** is a value passed during function invocation.
- The first statement of the function body can optionally* be a [[Python/data types/strings/strings|string]] [[literals|literal]] that acts as the function’s documentation string, or [[docstrings|docstring]].
	- \*[[docstrings]] aren't syntactically required, but you *must* add them to every function definition.


- Python provides the following types of functions:
	- Built-in functions
		- These functions are always available.
	- Functions defined in built-in [[Modules|modules]]
	- User-defined functions


