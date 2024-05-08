`while` loop is an indefinite iteration that is used when a loop repeats unknown number of times and end when some condition is met.
- The `while` statement loops until a condition is `False`.

syntax:
```Python
while <bool_expr>:
	<suite>
```
With the while loop we can execute a set of statements as long as a condition is true.

- The while loop requires relevant variables to be read.

Example:
```Python
i = 1
while i < 6:
  print(i)
  i += 1
```
## while-else
- With the else statement we can run a [[suite]] once, when the [[Boolean|boolean expression]] no longer is `True`:

```Python
i = 1
while i < 6:
  print(i)
  i += 1
else:
  print("i is no longer less than 6")
```

## break
- With the break statement we can stop the loop even if the while condition is `True`.
- `break` may only occur syntactically nested in a `for` or `while` loop, but not nested in a [[Python/Functions/Functions|function]] or [[Classes and objects#Classes|class]] definition within that loop.
- It **terminates** the nearest enclosing loop, skipping the optional `else` clause if the loop has one.
Example: 
```Python
i = 1
while i < 6:
    print(i)
    if i == 3:
        break
    i += 1
```

Another example:
```Python
i = 1
while i < 6:
    if i == 3:
        break
    print(i)
    i += 1
```
## continue
- With the continue statement we can stop the current iteration, and continue with the next.
- When encountered, the loop starts next iteration without executing the remaining statements in the current iteration.

Example:
```Python
i = 0
while i < 6:
  i += 1
  if i == 3:
    continue
  print(i)
```
## while vs for
> If you can iterate, do `for`, otherwise do `while

- `while` is useful in scenarios where the `break` condition doesn't logically depend on any kind of [[Iterable#Sequences|sequence]]. 
- When you're iterating over some kind of [[Iterable|collection]], it is usually better to use one of Python's iteration tools (use [[for]]).

[python - Why avoid while loops? - Stack Overflow](https://stackoverflow.com/questions/4270167/why-avoid-while-loops)

[loops - When to use "while" or "for" in Python - Stack Overflow](https://stackoverflow.com/questions/920645/when-to-use-while-or-for-in-python)
