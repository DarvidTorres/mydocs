# Implicit casting
When any language compiler/interpreter automatically converts object of one type into other, it is called automatic or implicit casting.

Note that memory requirement of each data type is different. For example, an integer object in Python occupies 4 bytes of memory, while a float object needs 8 bytes because of its fractional part. Hence, Python interpreter doesn't automatically convert a float to `int`, because it will result in loss of data. On the other hand, `int` can be easily converted into float by setting its fractional part to 0.

- Implicit casting is limited to `int` to `float` conversion.

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
