- An integer is an [[Python/OOP/Objects|object]], an instance of the `int` [[Classes|class]]
- The `int` class provides multiple constructors:

```python
int(10)
int(-10)
int(10.9) # gets truncated
int(-10.9) # gets truncated
int("10")
```

Set base with second argument:
```Python
int("1010", 2)
int("1010", base = 2)
int("A12F", base = 16)
int("534", base = 8)
int("A", base = 11)
```

Change integer from base 10 to another base:
```Python
bin(10) # Prefix "0b" to indicate binary
oct(10) # 0o12 prefix "0o"
hex(10) # prefix 0x
print(b := 0b101)
```

