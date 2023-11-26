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

An f-string expression can’t be empty:

```Python
f'foo{}bar'
SyntaxError: f-string: empty expression not allowed
```

An f-string expression (what's inside the curly brackets) cannot include a backslash `\`. Among other things, that means you can’t use a backslash escape sequence in an f-string expression:

```Python
f"newline: {ord('\n')}"
# SyntaxError: f-string expression part cannot include a backslash
```

but we can put the backslash into a variable as a workaround:

```Python
a = '\n'
print(f'New line: {a}')
```

The interpreter treats the remainder of the f-string—anything not inside curly braces—just as it would an ordinary string. For example, backlash (escape sequences) are processed as expected:

```Python
s = 'bar'
print(f'foo\n{s}')
```

We can escape curly braces using double curly braces ``{{}}``:

```Python
print(f'{{}}')
```

Examples:

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

we can make explicit the definition of variables

```Python
a = [1, 2 ,3]
b = {'foo': 1, 'bar': 2}
print(f'{a}')
print(f'{b}')
```

You may prefix an f-string with 'r' or 'R' to indicate that it is a raw f-string. In that case, backslash sequences are left intact, just like with an ordinary string. You can specify the `'r'` first and then the `'f'`, or vice-versa.

```Python
print(rf'foo\n')
print(fr'bar\n')
```

