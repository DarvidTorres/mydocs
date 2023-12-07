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
## walrus
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

Consider the following:
```Python
Foo, Bar = 2, 3
print(Foo, Bar)
Foo = Foo + Bar
print(Foo)
```

syntax
```Python
<var0> += <value | var1>
```
Add right side operand with left side operand and then assign to left operand

Example:
```Python
a, b = 2, 3
print(a, b)
# a = a + b
a += b
print(a)
```

## Unpack a collection

If you have a collection of values in a [[lists|list]], tuple, etc. Python allows you to extract the values into variables. This is called unpacking.

```Python
fruits = ["apple", "banana", "cherry"]
x, y, z = fruits
print(x, y, z)
```



