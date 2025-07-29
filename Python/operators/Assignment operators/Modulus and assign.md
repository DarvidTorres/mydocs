- Use the `%` operator to obtain the [[Arithmetic operators#Modulus and Floor division|modulus]], and then assign result.
syntax:
```Python
x = x % y
```

Example:
```Python
a, b = 2, 3
print(a, b)
a = a % b
print(a)
```

- Take the modulus using the left and the right operands and then assign the result (remainder) to the left operand.
```Python
x %= y
```

Example:
```Python
a, b = 2, 3
print(a, b)
# a = a % b
a %= b
print(a)
```