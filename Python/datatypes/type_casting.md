# Implicit casting
When any language compiler/interpreter automatically converts object of one type into other, it is called automatic or implicit casting.

Note that memory requirement of each data type is different. For example, an integer object in Python occupies 4 bytes of memory, while a float object needs 8 bytes because of its fractional part. Hence, Python interpreter doesn't automatically convert a float to `int`, because it will result in loss of data. On the other hand, `int` can be easily converted into float by setting its fractional part to 0.

- Implicit casting is limited to convert from `int` to `float` conversion.

Example:
```Python
print(type(a := 10))
print(type(b := 10.5))
print(type(a + b))
```

- Any other conversion won't be performed automatically.

Example:
```Python
'12' + 13
```

In implicit type casting, a Python object with lesser byte size is upgraded to match the bigger byte size of other object in the operation. For example, a `boolean` object is first upgraded to `int` and then to `float`, before the addition with a floating point object. In the following example, we try to add a `boolean` object with a `float`, note that `True` is equal to 1, and `False` is equal to 0.

```Python
print(type(c := True))
print(type(b := 10.5))
print(type(c + b))
```

# Explicit casting
There may be times when you want to specify a type on to a variable. This can be done with casting.
- Python is an object-orientated language, and as such it uses classes to define data types, including its primitive types.

| Sr.No.                | Function & Description                                                  |
| --------------------- | ----------------------------------------------------------------------- |
| `int(x [,base])`        | Converts x to an integer. base specifies the base if x is a string.     |
| `long(x [,base] )`      | Converts x to a long integer. base specifies the base if x is a string. |
| `float(x)`              | Converts x to a floating-point number.                                  |
| `complex(real [,imag])` | Creates a complex number.                                               |
| `str(x)`                | Converts object x to a string representation.                           |
| `repr(x)`               | Converts object x to an expression string.                              |
| `eval(str)`             | Evaluates a string and returns an object.                               |
| `tuple(s)`              | Converts s to a tuple.                                                  |
| `list(s)`               | Converts s to a list.                                                   |
| `set(s)`                | Converts s to a set.                                                    |
| `dict(d)`               | Creates a dictionary. d must be a sequence of (key,value) tuples.       |
| `frozenset(s)`          | Converts s to a frozen set.                                             |
| `chr(x)`                | Converts an integer to a character.                                     |
| `unichr(x)`             | Converts an integer to a Unicode character.                             |
| `ord(x)`                | Converts a single character to its integer value.                       |
| `hex(x)`                | Converts an integer to a hexadecimal string.                            |
| `oct(x)`                | Converts an integer to an octal string.                                 |

## int()

syntax:
```python
int ([<number>, [<base>]])
```

- `float` to `int`:
```Python
print(type(a := 10.5))
print(type(int(a))) #converts a float object to int
```

- `string` to `int`:
```Python
print(type(b := "100"))
print(type(int(b))) #converts a string object to int
```

- if the `string` contains a non-integer representation, Python raises ValueError.
```Python
print(type(a := "10.5"))
print(type(int(a)))
```

- binary, hex and octal `string` to `int`:
```Python
print(int("10001", 2)) # binary base 2
print(int("0o21", 8)) # octal base 8
print(int("0x11", 16)) # hexadecimal base 16
```
