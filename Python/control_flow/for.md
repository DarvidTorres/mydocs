Iterate over the items of an [[Iterables|iterable]].

syntax:
```Python
for <iterating_var> in <sequence>:
	<suite>
```

Example using string:
```Python
myString = "Foo"
for i in myString:
	print(i)
```

Example using list:
```Python
myList = ['Foo', 'Bar']
for i in myList:
	print(i)
```

- The `for` loop does not require an indexing variable to set beforehand, like the [[while#while vs for|while]] loop does.

## for-else
- The `else` statement is executed when the [[Iterables|iterable]] is exhausted, then the loop terminates.

Example:
```Python
for i in range(3):
    print(i)
else:
    print("end of loop")
```

## break
- With the `break` statement we can stop the loop before it has looped through all the items.

Example:
```Python
for i in range(3):
	print(i)
	if i == 1:
	    continue
```

## continue
- With the continue statement we can stop the current iteration, and continue with the next.
- When encountered, the loop starts next iteration without executing the remaining statements in the current iteration.

Example:
```Python
for i in range(3):
	if i == 1:
		continue
	print(i)
```

## pass
- `pass` is a null operation — when it is executed, nothing happens. It is useful as a placeholder when a statement is required syntactically, but no code needs to be executed.

`for` loops cannot be empty, but if you for some reason have a for loop with no content, put in the `pass` statement to avoid getting an error.

Example:
```Python
for i in range(2):
	pass
```

### Ellipses

We can use `...` in place of the `pass` statement

Example:
```Python
for i in range(2):
	...
```