- A Python tuple is a sequence of comma separated items, enclosed in parentheses `()`.
- Python tuples may have objects of **different** [[data types]].
- It is an **ordered** collection of items.
- Each item in the tuple has a unique position **index**, starting from 0.
- Tuples are **immutable**.
	- Any item from the tuple can be accessed using its index, **but** cannot be modified, removed or added.
- Tuples allow **duplicate** values.

Example:
```Python
myString = "string"
myFloat = 2.32
myIntA = 3
myIntB = 3
myComplex = 1+2j
myBool = True
myTuple = (myString, myFloat, myIntA, myIntB, myComplex, myBool)
print(myTuple)
print(type(myTuple))
```

## singleton
When creating a tuple with only one item, remember to include a comma after the item, otherwise it will not be identified as a tuple:

```Python
print(type(FalseTuple := ("a"))) # string
print(type(TrueTuple := ("a",))) # tuple
```

## modify a tuple

- Tuples are **unchangeable**, or **immutable** as it also is called.
	- But there is a workaround. Convert the tuple into a list, change the list, and convert the list back into a tuple.
