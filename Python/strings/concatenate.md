# concatenate

Strings can be concatenated (glued together) with the `+` operator, and repeated with `*`:

```Python
print(3 * 'un' + 'ium') # 3 times 'un', followed by 'ium'
```

Two or more _string literals_ (i.e. the ones enclosed between quotes) next to each other are automatically concatenated.

```Python
print('a' '3')
```

This feature is particularly useful when you want to break long strings:

```Python
text = ('Put several strings within parentheses '
        'to have them joined together.')
print(text)
```

It won't work if you add a new line without an endquote:

```Python
text = ('Put several strings within parentheses
        to have them joined together.')
print(text)
```

If you want to concatenate variables or a variable and a literal, use `+`:

```Python
prefix = 'Py'
print(prefix + 'thon')
```

