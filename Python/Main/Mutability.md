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

```python
def modify_list(lst):
	print(f"Initial lst #: {hex(id(lst))}")
	lst.append(100)
	print(f"Final lst #: {hex(id(lst))}")

print(my_list := [1, 2, 3])
print(f"my_list #: {hex(id(my_list))}")
modify_list(my_list)
print(f"my_list #: {hex(id(my_list))}")
my_list
```
Note: In this example, when modifying the temporary variable `lst`, its address changes and the address of the underlying variable `my_list` also changes.

```python
def modify_tuple(t):
	print(f"Initial t #: {hex(id(t))}")
	t[0].append(100) # Assumes first item is list
	print(f"Final t #: {hex(id(t))}")

print(my_tuple := ([1, 2, 3], 'a'))
print(f"my_tuple #: {hex(id(my_tuple))}")
modify_tuple(my_tuple)
print(f"my_tuple #: {hex(id(my_tuple))}")
my_tuple
```
Note: Since a tuple is an immutable object, its address remain, while the first item is mutable and thus we can alter its state.
