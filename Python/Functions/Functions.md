- A function is a block of code which only runs when it is called.

- Python provides the following types of functions:
	- Built-in functions
		- These functions are always available.
	- Functions defined in built-in [[Modules|modules]]
	- User-defined functions

- Function objects are created by function definition.

syntax:
```Python
def <function_identifier>([parameter(s)])
	["""<docstring>"""]
	<suite>
	[return [<return value>]]
```
- The keyword `def` introduces a function definition.
- Follow the naming convention `lowercase_with_underscores` for function identifiers.
- You can pass data, known as parameters, into a function.
	- Optionally, pass multiple parameters with comma separation.
		- By default, parameters have a positional behavior and you need to inform them in the same order that they were defined.
	- A **parameter** is a variable in a function definition.
		- It is a placeholder and hence does not have a concrete value.
	- An **argument** is a value passed during function invocation.
- The first statement of the function body can optionally* be a [[Python/data types/strings/strings|string]] [[literals|literal]] that acts as the function’s documentation string, or [[docstrings|docstring]].
	- \*[[docstrings]] aren't syntactically required, but you *must* add them to every function definition.

In general, a function takes arguments (if any), performs some operations, and returns a value (or object).

- Use the `return` statement to make functions send objects back to the caller code. These objects are known as the function’s return value. You can use them to perform further computation in your programs.
	- A `return` statement is used to end the execution of the function call and “returns” the result (value of the expression following the return keyword) to the caller.
	- All Python functions have a return value, either explicit or implicit.
	- `return` without an value returns `None`. No `return` keyword and the function returns `None`

Example:
```Python
def subtract(x, y):
	"""Return the subtraction of passed args"""
	r = x - y
	return r

print(subtract(2, 3))
print(subtract(3, 1))
```


