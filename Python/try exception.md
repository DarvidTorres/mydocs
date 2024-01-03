A Python program terminates as soon as it encounters an error. In Python, an error can be a syntax error or an exception.

- Syntax errors occur when the parser detects an incorrect statement.

Example:
```Python
print("Hello World"))
```

- An exception error occurs whenever syntactically correct Python code results in an error.

Example:
```Python
print(0 / 0)
```
Note: Python details what type of exception error was encountered.

Python comes with various built-in exceptions as well as the possibility to create self-defined exceptions.

- Use `raise` to throw an exception if a condition occurs.