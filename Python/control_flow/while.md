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

## break
- With the break statement we can stop the loop even if the while condition is `True`.
- The break statement can be used in both while and [[for]] loops.

Example: 
```Python
i = 1
while i < 6:
  print(i)
  if i == 3:
    break
  i += 1
```

## continue
- With the continue statement we can stop the current iteration, and continue with the next:

## while vs for
> If you can iterate, do `for`, otherwise do `while

- `while` is useful in scenarios where the `break` condition doesn't logically depend on any kind of [[Iterables#Sequences|sequence]]. 
- When you're iterating over some kind of [[Iterables|collection]], it is usually better to use one of Python's iteration tools (use [[for]]).

[python - Why avoid while loops? - Stack Overflow](https://stackoverflow.com/questions/4270167/why-avoid-while-loops)

[loops - When to use "while" or "for" in Python - Stack Overflow](https://stackoverflow.com/questions/920645/when-to-use-while-or-for-in-python)
