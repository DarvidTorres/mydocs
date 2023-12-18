- A lambda function is a small anonymous (without identifier) function.
- Can have any number of arguments but only one expression, which is evaluated and returned.
- Use lambda functions wherever function objects are required.
- Lambda functions are syntactically restricted to a single expression.

syntax:
```Python
lambda <*args> : <fx_body>
```

- Lambda functions are frequently used with [higher-order functions](https://en.wikipedia.org/wiki/Higher-order_function), which take one or more functions as arguments or return one or more functions.

Example:
```Python
def add_counter(n):
	lambda x += n
add_counter(3)
```
