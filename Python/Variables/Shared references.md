- [[Mutability|Immutable]] objects will share memory [[Python/Memory/address|address]], while [[Mutability|immutable]] objects will not.

Example with immutable objects:
```python
a = "Foo"
b = "Foo"
hex(id(a))
hex(id(b)) # Same addres though DON'T COUNT ON IT
b = "Foo Bar"
hex(id(a)) # Address remain
hex(id(b)) # changed address
```

Not always will immutable objects share memory address:
```python
a = 500
b = 500
hex(id(a))
hex(id(b))
```

Example with mutable objects:
```Python
a = [1, 2, 3]
b = [1, 2, 3]
hex(id(a))
hex(id(b))
```

```Python
print(a := [1, 2, 3])
b = a
hex(id(a))
hex(id(b))
b.append(100)
hex(id(a))
hex(id(b))
print(a)
```
Note: When modifying `b`, since the value changed, but not the address, `a` is also altered.

## None

The `None` object can be assigned to variables to indicate that they are not set (in the way that we would expect them to be).

The memory manager will **always** use a shared reference when assigning a variable to `None`.