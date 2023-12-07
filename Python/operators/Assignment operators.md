## Assignment
syntax:
```Python
<identifier> = <value>
```

Example:
```Python
myVar = 'value'
print(myVar)
```
## multiple assignment
- assign values to multiple variables in one line:
```Python
a, b, c = 'Foo', 'Bar', 'Baz'
print(a, b, c)
```
Note: The number of variables must match the number of values.

- Assign the same value to multiple variables in one line:
```Python
x = y = z = "Orange"
print(x, y, z)
```
## Walrus
- Assignment expressions allow you to assign and return a value in the same expression.

syntax:
```Python
<identifier> := <value>
```

Example:
```Python
print(walrus := "I am the walrus")
```
Note: The walrus only makes certain constructs more convenient, and can sometimes communicate the intent of your code more clearly.

The following is a bad usage example:
```Python
inputs = list()
while (current := input("Write something: ")) != "quit":
    inputs.append(current)
```
Use your best judgement about when the walrus operator helps make your code more readable.
## Add and Assign

- Use the `+` operator to add values, and then assign result.
syntax:
```Python
x = x + y
```

Example:
```Python
a, b = 2, 3
print(a, b)
a = a + b
print(a)
```

- Add right side operand with left side operand and then assign to left operand
syntax
```Python
x += y
```

Example:
```Python
a, b = 2, 3
print(a, b)
# a = a + b
a += b
print(a)
```

## Subtract and Assign
- Use the `-` operator to substract values, and then assign result.
syntax:
```Python
x = x - y
```

Example:
```Python
a, b = 2, 3
print(a, b)
a = a - b
print(a)
```

- Subtract the right operand from the left operand and then assign the result to the left operand.
syntax
```Python
x -= y
```

Example:
```Python
a, b = 2, 3
print(a, b)
# a = a - b
a -= b
print(a)
```

## Multiply and Assign
- Use the `*` operator to multiply values, and then assign result.
syntax:
```Python
x = x * y
```

Example:
```Python
a, b = 2, 3
print(a, b)
a = a * b
print(a)
```

* Multiply the right operand with the left operand and then assign the result to the left operand.
syntax
```Python
x *= y
```

Example:
```Python
a, b = 2, 3
print(a, b)
# a = a * b
a *= b
print(a)
```

## Exponent and Assign
- Use the `**` operator to obtain the exponent (raise power) value, and then assign result.
syntax:
```Python
x = x ** y
```

Example:
```Python
a, b = 2, 3
print(a, b)
a = a ** b
print(a)
```

- Calculate the exponent (raise power) value using operands and then assigning the result to the left operand.
```Python
x **= y
```

Example:
```Python
a, b = 2, 3
print(a, b)
# a = a ** b
a **= b
print(a)
```

## Divide and Assign
- Use the `/` operator to divide values, and then assign result.
syntax:
```Python
x = x / y
```

Example:
```Python
a, b = 2, 3
print(a, b)
a = a / b
print(a)
```

- Divide the left operand with the right operand and then assig the result to the left operand.
syntax
```Python
x /= y
```

Example:
```Python
a, b = 2, 3
print(a, b)
# a = a / b
a /= b
print(a)
```

## Floor division and Assign
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
## Modulus and Assign
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