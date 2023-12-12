
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

- We can combine positional-only, regular, and keyword-only arguments in that order:
```Python
def combine_args(positional_arg, /, regular_arg, *, keyword_arg):
	"""Print passed arguments"""
	print(positional_arg, regular_arg, keyword_arg)
	
combine_args('positional', 'regular', keyword_arg='keyword_arg')
```