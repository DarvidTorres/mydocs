The `is` keyword compare two objects and return `True` if both the objects are pointing to the same memory address else return `False`. This is not the same as the equality (`==`) operator, which compares the actual value stored in the object.

```python
a = "Foo"
b = "Bar"
c = a
print(f"a address: {hex(id(a))}")
print(f"b address: {hex(id(b))}")
print(f"c address: {hex(id(c))}")
a is b
a is c
```

Example with float:
```python
a = 10
b = 10.0
type(a)
type(b)
a is b
a == b
```