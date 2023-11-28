# quotes

To quote a quote, we need to “escape” it, by preceding it with `\`. Alternatively, we can use the other type of quotation marks:

```Python
print('doesn\'t') # use \' to escape the single quote...
print("doesn't") # or use double quotes instead
print('"Yes," they said')
print("\"Yes,\" they said.")
print('"Isn\'t," they said.')
```
# raw strings

If you don’t want characters prefaced by `\` to be interpreted as special characters, you can use raw strings by adding an r before the first quote:

```Python
print('C:\some\name')  # here \n means newline!
print(r'C:\some\name')  # note the r before the quote
```
There is one subtle aspect to raw strings: a raw string may not end in an odd number of `\` characters; see the [FAQ](https://docs.python.org/3/faq/programming.html#faq-programming-raw-string-backslash) for more information and workarounds.

# multiline

String literals can span multiple lines using triple-quotes:

```Python
print("""a\
b
c
""")

print('''d
e\
f
''')
```

End of lines are automatically included in the string, but it’s possible to prevent this by adding a \ at the end of the line.

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

Strings can be indexed, with the first character having index 0. There is no separate character type; a character is simply a string of size one:

```Python
word = 'Python'
print(word[0]) # character in position 0
print(word[1:3]) # characters in closed-open range
```

Notice in the example above that ranges in python are closed-open (it includes the first component, but not the last).

Indices may also be negative numbers, to start counting from the right:

```Python
word = 'Python'
print(word[-0]) # first character print(0 == -0)
print(word[-1]) # last character
print(word[-3:-1]) # -3<-1
print(word[-1:-3]) # nothing gets printed
print(word[-5:3]) # nothing gets printed
```

Note that since -0 is the same as 0, negative indices start from -1. Also notice that negative ranges have to be ordered from less to higher value otherwise nothing gets printed.

Slice indices have useful defaults; an omitted first index defaults to zero, an omitted second index defaults to the size of the string being sliced.

```Python
word = 'Python'
print(word[:2])
print(word[4:])
print(word[-2:])
print(word[:-1])
```

Note how the start is always included, and the end always excluded. Let `s` be a string, then `s[:i]` + `s[i:]` is always equal to `s`:

```Python
word = 'Python'
print(word[:2] + word[2:])
```