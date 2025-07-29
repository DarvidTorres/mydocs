- Set in Python also a [[Iterable|collection]] [[data types|data type]] such as [[lists|list]] or [[tuples|tuple]].
- A set object is a collection of one or more objects enclosed within curly brackets `{}`.
- Sets are **not** an ordered collection,
	- Items in a set are **not** accessible by its positional index.
- Existing items are unchangeable, but can be removed from the set and more can be added. 

Example:
```Python
myString = "string"
myFloat = 2.32
myIntA = 3
myIntB = 3
myComplex = 1+2j
myBool = True
mySet = {myString, myFloat, myIntA, myIntB, myComplex, myBool}
print(mySet)
print(type(mySet))
```
Note that in the example above, only one `3` of the `myIntA` and `myIntB` variables is printed.

- Duplicate values will be ignored:
```Python
print(TrueSet := {True, 1})
print(FalseSet := {False, 0})
print(len((TrueSet, FalseSet))) # Note double parenthesis () in len() arg
```
- The values `True` and $1$ are considered the same value in sets, and are treated as duplicates.
- The values `False` and $0$ are considered the same value in sets, and are treated as duplicates.

- No access to items in a set by referring to an index or a key.
	- But can loop through the set items using a [[for|for loop]], or
	- ask if a specified value is present in a set, by using the `in` keyword.

```Python
mySet = {'Foo', 'Bar', 'Baz'}
for n in mySet:
    print(n, n in mySet)
```

- Set items are unchangeable, but you can remove items and add new items.
- The `add()` method in set class adds a new element.
	- If the element is already present in the set, there is no change in the set.

```Python
print(mySet := {'Foo'})
mySet.add('Foo')
mySet.add('Bar')
print(mySet)
```

- Union of sets using the `union()` method:
```Python
print(mySet0 := {'Foo'})
print(mySet1 := {'Bar'})
print(mySet2 := mySet0.union(mySet1))
```

- To add items from another set into the current set, use the `update()` method:
```Python
print(mySet0 := {'Foo'})
print(mySet1 := {'Bar'})
mySet0.update(mySet1)
print(mySet0)
```
The object in the `update()` method does not have to be a set, it can be any iterable object (tuples, lists, dictionaries etc.):
```Python
print(mySet0 := {'Foo'})
print(mySet1 := ['Bar'])
mySet0.update(mySet1)
print(mySet0)
```

- To remove an item in a set, use the `remove()`, or the `discard()` method.
```Python
print(mySet := {'Foo', 'Bar', 'Baz'})
mySet.remove('Baz')
mySet.discard('Bar')
print(mySet)
```

- You can also use the `pop()` method to remove an item, but this method will remove a random item, so you cannot be sure what item that gets removed.
```Python
print(mySet := {'Foo', 'Bar', 'Baz'})
print(mySet.pop())
print(mySet)
```
Note: The return value of the pop() method is the removed item.