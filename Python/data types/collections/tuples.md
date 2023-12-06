- A Python tuple is a sequence of comma separated items, enclosed in parentheses `()`.
- Python tuples may have objects of **different** [[data types]].
- It is an **ordered** collection of items.
- Each item in the tuple has a unique position **index**, starting from 0.
- Tuples are **immutable**.
	- Any item from the tuple can be accessed using its index, **but** cannot be modified, removed or added.
- Tuples allow **duplicate** values.

Example:
````Python
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
