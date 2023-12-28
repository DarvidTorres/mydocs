
- Python has a built-in `help()` function
- IPython introduces the `?` character as a shorthand for accessing documentation.

Example:
```IPython
len?
```

```IPython
L = [1, 2, 3]
L.insert?
```

The `?` mark can be used to access to documentation via [[docstrings]].

Example:
```IPython
def square(a):
	"""Return the square of a."""
	return a ** 2
square?
```

- Access source code with double question mark (`??`).

Example:
```IPython
def square(a):
	"""Return the square of a."""
	return a ** 2
square??
```

Sometimes the `??` suffix doesn't display any source code, in general, because the object in question is not implemented in Python, but in C or some other compiled extension language. If this is the case, the `??` suffix gives the same output as the `?` suffix.

Example:

```IPython
len??
```

