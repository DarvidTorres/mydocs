- A Python list is a sequence of comma separated items, enclosed in square brackets `[]`.
- Python lists may have objects of **different** [[data types]].
- It is an **ordered** collection of items.

Example
```Python
myString = "string"
myFloat = 2.32
myInt = 3
myComplex = 1+2j
myBool = True
myList = [myString, myFloat, myInt, myComplex, myBool]
print(myList)
```

- Each item in a list has a unique position **index**, starting from 0.
- Lists are **mutable**.
	- Items can be accessed using its index, and can be modified.
Example:
```Python
mylist = ['Foo']
print(mylist)
mylist[0] = 'Bar'
print(mylist)
```

- Assignment to slices is possible:
```Python
letters = ['a', 'b', 'c', 'd', 'e', 'f', 'g']
print(letters)
letters[2:5] = ['C', 'D', 'E']
print(letters)
letters[2:5] = []
print(letters)
letters[:] = []
print(letters)
```

- Add new items at the end of the list, by using the `append()` method:
```Python
mylist = ["a"]
print(mylist)
mylist.append(2.0**3)
print(mylist)
```

- Concatenate two lists with `+` [[Python/operators/operators|operator]]:
```Python
print([1, 2, 3] + [4, 5, 6])
```

- Concatenate multiple copies of a list with `*` operator:
```Python
print(['Hi!'] * 4)
```

- The membership operators `in` and `not in` work with list object:
```Python
3 in [1, 2, 3]
```
