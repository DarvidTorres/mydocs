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
