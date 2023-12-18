- A lambda function is a small anonymous (without identifier) function.
- Can have any number of arguments but only one expression, which is evaluated and returned.
- Use lambda functions wherever function objects are required.
- Lambda functions are syntactically restricted to a single expression.

syntax:
```Python
lambda <*args> : <single_line_expr>
```

- Lambda functions are frequently used with [higher-order functions](https://en.wikipedia.org/wiki/Higher-order_function), which take one or more functions as arguments or return one or more functions.

Example:
```Python
def high_ord_func(n):
	"""Return a lambda function with arg n"""
    return lambda x: x + n

print(type(high_ord_func(3)))
print(high_ord_func(3)(2))
```
Note: `high_ord_func` is returning a function, in the example, with actual argument `3` passed for the formal `n` argument, and thus, what's returned from `high_ord_func(3)` is `lambda x: x + 3`, which is a function. Then, if we pass argument `2` to that function we get `2 + 3`.

We can assign an identifier to `lambda` functions:

```Python
def high_ord_func(n):
    return lambda x: x + n

f = high_ord_func(3)
print(f(2))
```
