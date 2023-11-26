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

A single quote is escaped with a backslash character.

```Python
print(f'This was a \'great\' film')
```

You may prefix an f-string with 'r' or 'R' to indicate that it is a raw f-string. In that case, backslash sequences are left intact, just like with an ordinary string. You can specify the `'r'` first and then the `'f'`, or vice-versa.

```Python
print(rf'foo\n')
print(fr'bar\n')
```

F-string also makes debugging easier too. Instead of printing the variable name and its value, we only need to write the variable inside the f-string `{variable_name=}`:

```Python
a = 10
print(f'{a = }')
```

We can do arithmetic operations inside f-string expressions:

```Python
x = 2
print(f'{x} cubed is {x**3}')
```

We can also call functions in f-strings.

```Python
def mymax(x, y):

    return x if x > y else y

a = 3
b = 4

print(f'Max of {a} and {b} is {mymax(a, b)}')
```

we can make explicit the definition of variables

```Python
a = [1, 2 ,3]
b = {'foo': 1, 'bar': 2}
print(f'{a}')
print(f'{b}')
```

# Formatting

To format f-string expressions use the following:

Syntax:
```Python
f'{<variable | value>:[width][.precision][type]}'

#You need to specify precision only in case of floating point numbers
```

The type can be used with format codes:

`d` for integers
`f` for floating-point numbers
`b` for binary numbers
`o` for octal numbers
`x` for octal hexadecimal numbers
`s` for string
`e` for floating-point in an exponent format

## Alignment

To align text (left or right) we use the `width` element (see syntax above), which can be specified using the following:

| Option | Meaning                                                                                                                                                                                                                                                                            |
| ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `<`    | Forces the field to be left-aligned within the available space (this is the default for most objects).                                                                                                                                                                             |
| `>`    | Forces the field to be right-aligned within the available space (this is the default for numbers).                                                                                                                                                                                 |
|`^`|Forces the field to be centered within the available space.|
| `=`    | Forces the padding to be placed after the sign (if any) but before the digits. This is used for printing fields in the form ‘+000000120’. This alignment option is only valid for numeric types. It becomes the default for numbers when ‘0’ immediately precedes the field width. |


Example:

```Python
a = 3
print(f'{a:>5}'')
```

In the example above, the option `>` forces the output to be a string of size five, where the value `a` is at the rightmost position, and the rest (four) characters (to the left of `a`) are spaces (by default). We can define which character will pad the string:

```Python
a = 3
print(f'{a:>5}')
print(f'{a:#>5}')
print(f'{a:$>5}')
print(f'{a:%>5}')
print(f'{a:_>5}')
```

The same applies for `<`:

```Python
a = 3
print(f'{a:<5}')
print(f'{a:#<5}')
print(f'{a:$<5}')
print(f'{a:%<5}')
print(f'{a:_<5}')
```

