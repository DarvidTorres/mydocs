# String interpolation

The process of evaluating a string literal containing one or more placeholders, yielding a result in which the placeholders are replaced with their corresponding values.

# f-strings

formatted string literals (f-strings).

- To create an f-string, prefix the string with the letter `f` or the uppercase `F`.

Example: 

```Python
f'foo bar baz'

F'qux quux'
```

Just like with any other type of string, you can use single, double, or triple quotes to define an f-string:

```Python
f'foo'
f"bar"
f'''baz'''
```

Any portion of an f-string that’s enclosed in curly braces ``{}`` is treated as an "f-string expression". The expression is evaluated and converted to string representation, and the result is interpolated into the original string in that location:

```Python
s = 'bar'
print(f'foo {s}')
```

An f-string expression (what's inside the curly brackets) cannot include a backslash, but we can put the backslash into a variable as a workaround:

```Python
newline = ord('\n')

print(f"newline: {newline}")
```

The interpreter treats the remainder of the f-string—anything not inside curly braces—just as it would an ordinary string. For example, backlash (escape sequences) are processed as expected:

```Python
s = 'bar'
print(f'foo\n{s}\nbaz')
```

Example:

```Python
quantity = 6
item = 'bananas'
price = 1.74
print(f'{quantity} {item} cost ${price}')
```

we can do arithmetic operations inside f-string expressions:

```Python
x = 2
print(f'{x} cubed is {x**3}')
```