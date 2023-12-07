There are four collection data types in the Python programming language:

- [[lists|List]] is a collection which is **ordered** and **changeable**. Allows **duplicate** members.
- [[tuples|Tuple]] is a collection which is **ordered** and **unchangeable**. Allows **duplicate** members.
- [[sets|Set]] is a collection which is **unordered**, **unchangeable**, and **unindexed**. **No duplicate** members.
- [[dictionaries|Dictionary]] is a collection which is **ordered** and changeable. **No duplicate** members.

## Unpack a collection

If you have a collection of values, Python allows you to extract the values into variables. This is called unpacking.

```Python
fruits = ["apple", "banana", "cherry"]
x, y, z = fruits
print(x, y, z)
```

