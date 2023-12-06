# if
syntax:
```Python
if <boolean_expression>:
	<suite>
```

if the [[boloean|boolean expression]] is `False`, the [[suite]] will not be executed.

Example: 
```Python
if (2 > 3): # A False boolean expression
    print("False") # Won't execute
```

```Python
if (2 < 3): # A True boolean expression
    print("True") # Will execute
```
# if else

```Python
if <boolean_expression>:
	<if_suite>
else:
	<else_suite>
```

- If the [[boloean|boolean expression]] is `True`, then `if_suite` will execute.
- If the [[boloean|boolean expression]] is `False`, then `else_suite` will execute.

```Python
if (2 > 3): # A False boolean expression
    print("if suite") # Won't execute
else:
    print("else suite") # Will execute
```

