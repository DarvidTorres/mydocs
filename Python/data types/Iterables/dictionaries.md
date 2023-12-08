- Python's dictionary is example of mapping type.
	- A mapping object 'maps' value of one object with another.
- A dictionary is a collection of `key:value` pairs.
	- The pairs are separated by comma and put inside curly brackets `{}`.
- A number, string or tuple can be used as key.
	- Keys are immutable
- Values can be of any type.
- Dictionaries do not allow duplicates,
	- cannot have two items with the same key
- Dictionaries are changeable,
	- we can change, add or remove items after the dictionary has been created.

Example:
```Python
print(myDict := {"Key": "Value"})
print(type(myDict))
```

- Duplicate values will overwrite existing values:
```Python
myDict = {
  "a": "Foo",
  "b": "Bar",
  "b": "Baz", # overwrites previous value
}
print(myDict)
```

- You can change the value (not the key) of a specific item by referring to its key name:
```Python
myDict = {
  "a": "Foo",
  "b": "Bar",
}
print(myDict)
myDict["b"] = "Baz"
print(myDict)
```

- Dictionary items can be referred to by using the key name:
```Python
myDict = {
  "a": "Foo",
  "b": "Bar",
}
print(myDict["a"])
```

- [[Iterables|Iteration]] on a dictionary runs over the `key` part of pairs.

- The `keys()` method will return a list of all the keys in the dictionary.
- The `values()` method will return a list of all the values in the dictionary.
- The `items()` method will return a list of all the `key:value` pairs in the dictionary.
```Python
myDict = {
  "a": "Foo",
  "b": "Bar",
}
print(myDict.keys())
print(myDict.values())
print(myDict.items())
```

- `dict_keys`, `dict_values` and `dict_items` classes are [[Iterables|iterable]].
