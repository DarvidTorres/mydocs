- A variable is a reference to a memory address.
- An identifier is an [[Alias|alias]] to a memory address.
- Values are saved in memory.
- **PEP8**: lowercase with words separated by underscores as necessary to improve readability.

```Python
my_var = "Foo"
id(my_var)
hex(id(my_var))
```

We can free memory addresses using `del`:
```Python
my_var = "Foo"
print(my_var)
del my_var
print(my_var)
```

