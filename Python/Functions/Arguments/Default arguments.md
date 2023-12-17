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

