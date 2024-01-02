- A Python list is a sequence of comma separated items, enclosed in square brackets `[]`.
- Python lists may have objects of **different** [[data types]].
- It is an **ordered** collection of items.
- Allow **duplicate** members.

Example
```Python
myString = "string"
myFloat = 2.32
myIntA = 3
myIntB = 3
myComplex = 1+2j
myBool = True
my_list = [myString, myFloat, myIntA, myIntB, myComplex, myBool]
print(my_list)
print(type(my_list))
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

- Concatenate two lists with `+` [[Python/Operators/Operators|operator]]:
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

# List comprehension

A list comprehension consists of brackets containing an expression followed by a [[for]] clause, then zero or more [[for]] or [[if]] clauses. The result will be a new list resulting from evaluating the expression in the context of the `for` and `if` clauses which follow it.

## Case 1: 

No [[Boolean|boolean expression]].

syntax:
```Python
[<expr> for <item> in <iterable>]
```

Example:
```Python
my_list = [x for x in range(1, 10)]
```
Each item from the [[Iterables|iterable]] is added to the list.
## Case 2:

One [[Boolean|boolean expression]].

syntax:
```Python
[<expr> for <item> in <iterable> if <bool_expr> == True]
```

Example:
```Python
my_list = [x for x in range(1, 10) if x % 2 == 0]
```
Only even numbers will be added to the list.

Example:
```Python
my_list = [x for x in range(1, 10) if x % 2 == 0 if x % 3 == 0]
```
Only even numbers that are multiple of 3 will be added to the list.

This is equivalent to:
```Python
my_list = []
for x in range(1, 10):
    if x % 2 == 0:
        if x % 3 == 0:
            my_list.append(x)
my_list
```

Example:
```Python
my_list = [x for x in range(1, 10) if x % 2 == 0 and x % 3 == 0]
```
Note: we can also use `or`.

Which is equivalent to:
```Python
my_list = []
for x in range(1, 10):
    if x % 2 == 0 and x % 3 == 0:
        my_list.append(x)
```

## Case 3

We can use the [[if#short hand if-else|ternary operator]]:

syntax:
```Python
[<ternary_operator> for <item> in <iterable>]
[<if_suite> if <bool_expr> else  for <item> in <iterable>]
```


