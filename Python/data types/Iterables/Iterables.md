
```mermaid
---
title: Iterables
---
flowchart LR
I(Iterables) --> S(Sequences)
	S --> Strings
	S --> Lists
	S --> Tuples
	S --> Range
	S --> Bytes
I(Iterables) --> C(Collections)
	C --> Dictionary
	C --> Sets

```
# Sequences

- A sequence is a positionally **ordered** collection of items.
- [[lists|Lists]], [[tuples|tuples]], and [[Python/data types/strings/strings|strings]] are sequences because things come out of them in the same order they were put in.
# Collections
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

