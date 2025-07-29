- Use the `//` operator to obtain the [[Arithmetic operators#Modulus and Floor division|floor division]], and then assign result.
syntax:
```Python
x = x // y
```

Example:
```Python
a, b = 2, 3
print(a, b)
a = a // b
print(a)
```

- Floor divide the left operand with the right operand and then assigning the result (quotient) to the left operand.
```Python
x //= y
```

Example:
```Python
a, b = 2, 3
print(a, b)
# a = a // b
a //= b
print(a)
```