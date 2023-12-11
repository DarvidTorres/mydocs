## Default arguments

- Python allows to define a function with default value assigned to one or more formal arguments.
- A default argument is a parameter that assumes a default value if a value is not provided in the function call for that argument.
- The function uses the default value for such an argument if no value is passed to it.
- If any value is passed, the default value is overridden with the actual value passed.

Example:
```Python
def default_args(x = 'Foo'):
    print(x)
    
default_args()
default_args('Bar')
```
## keyword arguments

- Python allows to pass function arguments in the form of keywords which are also called **named arguments.**

We can call the arguments using the formal identifiers:
Example:
```Python
def keyword_args(x, y):
	print(x, y)

keyword_args(x = 'Foo', y = 'Bar')
```

- By default, function arguments are positional and must be called in the defined order.
- When using keyword arguments, it is not necessary to follow the order of formal arguments in function definition.
- The idea is to allow the caller to specify the argument name with values so that the caller does not need to remember the order of parameters.

If we call arguments using the defined identifiers (names or keywords), we can change the order:
```Python
def subtract(x, y):
	"""Return the subtraction of passed args"""
	r = x - y
	return r

print(subtract(2, 3)) # Default order 2 - 3
print(subtract(x = 2, y = 3)) # 2 - 3
print(subtract(y = 2, x = 3)) # 3 - 2
```

We can, but should **avoid**, use mixed calling. 
- We can pass values to some arguments without keywords, and for others with keyword.

```Python
def subtract(x, y):
	"""Return the subtraction of passed args"""
	r = x - y
	return r

print(subtract(2, y = 3)
```

Positional arguments (the ones called without identifier) must follow position:
```Python
def subtract(x, y):
	"""Return the subtraction of passed args"""
	r = x - y
	return r

print(subtract(x = 2, 3))
```

```Python
def subtract(x, y):
	"""Return the subtraction of passed args"""
	r = x - y
	return r

print(subtract(2, x = 3))
```

## Positional-only arguments

- We can use `/` in the function definition to force that all arguments before it must be specified by position (and not by keyword argument).

Example:
```Python
def subtract(x, y, /):
	"""Return the subtraction of passed args"""
	r = x - y
	return r

print(subtract(x = 2, y = 3)) # keyword arguments yields error
```

## keyword-only arguments

- We can use `*` in the function definition to force that all arguments after it must be specified using a keyword

Example:
```Python
def subtract(*, x, y):
	"""Return the subtraction of passed args"""
	r = x - y
	return r

print(subtract(2, 3)) # positional arguments yields error
```

