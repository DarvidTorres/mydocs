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

```Python
x = 10
if x > 5:
	raise Exception("This is an exception")
```

- The `try` and `except` block in Python is used to catch and handle exceptions.
- Python executes code following the `try` statement as a normal part of the program.
- The code that follows the `except` statement is the program's response to any exceptions in the preceding `try` clause.

syntax:
```Python
try:
	<try_suite>
except:
	<executes_when_error_in_try_suite>
```

Example:
```Python
try:
  print(x)
except:
  print("An exception occurred")
```
Note: Since the try block raises an error, the except block will be executed.

- Use `else` to define a block of code to be executed if no errors were raised:

```Python
try:
  print("Hello")
except:
  print("Something went wrong")
else:
  print("Nothing went wrong")
```

- The `finally` block, if specified, will be executed regardless if the try block raises an error or not.
- 
```Python
try:
  print(x)
except:
  print("Something went wrong")
finally:
  print("The 'try except' is finished")
```

This can be useful to close objects and clean up resources:.

```Python
try:
  f = open("demofile.txt")
  try:
    f.write("Lorum Ipsum")
  except:
    print("Something went wrong when writing to the file")
  finally:
    f.close()
except:
  print("Something went wrong when opening the file")
```