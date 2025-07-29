- A function is a block of code which only runs when it is called.

- Python provides the following types of functions:
	- Built-in functions
		- These functions are always available.
	- Functions defined in built-in [[Modules|modules]]
	- User-defined functions


- Function objects are created by function definition.

- function identifiers must be `snake_case`.

syntax:
```Python
def <function_identifier>([parameter(s)])
	["""<docstring>"""]
	<suite>
	[return [<return_value>]]
```

- The keyword `def` introduces a function definition.
- **PEP8**: convention `lowercase_with_underscores` for function identifiers.
- You can pass data, known as parameters, into a function.
	- Optionally, pass **multiple parameters** with comma separation.
		- By default, parameters have a positional behavior and the function expects them (when invoked) in the same order as defined.
		- By default, a function must be called with the correct number of arguments.
	- A **parameter** is a variable in a function definition.
		- It is a placeholder and hence does not have a concrete value.
		- Also called **formal arguments**.
	- An **argument** is a value passed during function invocation.
		- Also called **actual arguments.**
- The first statement of the function body can optionally* be a [[Python/data types/Strings/strings|string]] [[literals|literal]] that acts as the function’s documentation string, or [[docstrings|docstring]].
	- \*[[docstrings#function docstrings|docstrings]] aren't syntactically required, but you *must* add them to every function definition.


A function takes arguments (if any), performs some operations, and returns a value (or [[Python/OOP/Objects|object]]).

- Use the `return` statement to make functions send objects back to the caller code. These objects are known as the function’s return value. You can use them to perform further computation in your programs.
- A `return` statement is used to end the execution of the function call and “returns” the result (value of the expression following the return keyword) to the caller.
- All Python functions have a return value, either explicit or implicit.
- `return` without an value returns `None`. No `return` keyword and the function returns `None`

Example:
```Python
def subtract(x, y):
	r = x - y
	return r

print(subtract(2, 3))
print(subtract(3, 2))
```

The function itself is an object, can be returned in an interactive display like [[IPython]], without calling arguments, only identifier:
```IPython
def my_fun():
	print("Foo")
	
my_fun # Return function object
type(my_fun)
my_fun() # Actual invokation
```

Functions can return functions:

```Python
def square(a):
	return a ** 2

def cube(a):
	return a ** 3

def select_function(a):
	if a == 1:
		return square
	else:
		return cube

f = select_function(1)
f is square
f(2)
f = select_function(2)
f is cube
f(2)
select_function(2)(3)
```

We can pass functions to functions as arguments:
```Python
def square(a):
	return a ** 2
	
def cube(a):
	return a ** 3
	
def exec_function(fn, n):
	return fn(n)

exec_function(cube, 2)
exec_function(square, 2)
```
## Annotations

We can annotate expected type as documentation to the function arguments, although it doesn't prevent the passing of other types:

```Python
def my_fun(a: int, b: int):
	print(a * b)
	
my_fun(2, 3)
my_fun('a', 3)
my_fun([1, 2], 3)
```


![[docstrings#function docstrings]]


