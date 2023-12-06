# slicing strings

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

Note how the start is always included, and the end always excluded. Let `s` be a string, then `s[:i]` + `s[i:]` is always equal to `s` for any `i` $\in \mathbb{Z}$:

```Python
word = 'Python'
print(word[:2] + word[2:])
```

The built-in function `len()` returns the length of a string:

```Python
s = 'supercalifragilisticexpialidocious'
len(s)
```
