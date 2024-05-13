- Changing the data inside an [[Python/OOP/Objects|object]] is called **modifying the internal state** of the object.
- When changing the value of a variable, the memory address doesn't change, only the internal state (data) has changed. We say that the object was mutated.
- An object whose internal state can be changed is called **mutable**.
- An object whose internal state cannot be changed is called immutable.

- Immutable Objects:
	- Numbers (int, float, complex)
	- Booleans
	- Strings
	- Tuples
	- Frozen Sets
	- Bytes
- Mutable Objects:
	- Lists
	- Dictionaries
	- Sets
	- Byte Arrays


```python
def process(s):
	print(f"Initial s #: {hex(id(s))}")
	s = s + " world"
	print(f"Final s #: {hex(id(s))}")

my_var = "hello"
print(f"my_var #: {hex(id(my_var))}")
process(my_var)
print(f"my_var #: {hex(id(my_var))}")
```
Note: In this example, when trying to modify a string, the memory address of the temporary variable `s` changes, while `my_var` address remains.




