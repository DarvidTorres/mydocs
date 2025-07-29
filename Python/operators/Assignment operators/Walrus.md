- Assign and return a value in the same expression.

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