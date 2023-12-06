# multiple assignment
- Python allows you to assign values to multiple variables in one line:
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

## Unpack a collection

If you have a collection of values in a [[lists|list]], tuple, etc. Python allows you to extract the values into variables. This is called unpacking.

```Python
fruits = ["apple", "banana", "cherry"]
x, y, z = fruits
print(x, y, z)
```
# walrus

* Assignment expressions are written using the walrus operator: `:=`.
* Assignment expressions allow you to assign and return a value in the same expression.

```Python
print(walrus := True)
type(walrus)
```

The walrus only makes certain constructs more convenient, and can sometimes communicate the intent of your code more clearly.

The following is a bad example:

```Python
inputs = list()
while (current := input("Write something: ")) != "quit":
    inputs.append(current)
```

Use your best judgement about when the walrus operator helps make your code more readable.

Some good examples:

```Python
# In this example, the assignment expression helps avoid calling len() twice
if (n := len(a)) > 10:
    print(f"List is too long ({n} elements, expected <= 10)")
```
