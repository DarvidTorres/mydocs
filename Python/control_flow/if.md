# if
syntax:
```Python
if <boolean_expression>:
	<suite>
```

if the [[Boolean|boolean expression]] is `False`, the [[suite]] will not be executed.

Example: 
```Python
if (2 > 3): # A False boolean expression
    print("False") # Won't execute
```

```Python
if (2 < 3): # A True boolean expression
    print("True") # Will execute
```
# if-else

syntax:
```Python
if <boolean_expression>:
	<if_suite>
else:
	<else_suite>
```

- If the [[Boolean|boolean expression]] is `True`, then `if_suite` will execute.
- If the [[Boolean|boolean expression]] is `False`, then `else_suite` will execute.

Example:
```Python
if (2 > 3): # A False boolean expression
    print("if suite") # Won't execute
else:
    print("else suite") # Will execute
```

# if-elif-else

syntax:
```Python
if <if_bool_expr>:
    <if_suite>
elif <elif_bool_expr>:
    <elif_suite_0>
else:
    <suite>
```

- If the `if_bool_expr` is `True`, then `if_suite` is executed.
- If the `if_bool_expr is `False` and the `elif_bool_expression` is `True`, then `elif_suite_0` will execute.
- If both `if_bool_expr` and `elif_bool_expr` are `False`, then `else_suite` will execute.

Example:
```Python
if (2 > 3):
    print("if suite")
elif (2 == 2):
    print("elif suite")
else:
    print("else suite")
```

We can have multiple `elif` expressions:
```Python
if (2 > 3):
    print("if suite")
elif (2 > 2):
    print("elif suite 0")
elif (2 > 1):
    print("elif suite 1")
else:
    print("else suite")
```

# short-hand if
Whenever there is only a single statement to be executed inside the if block then shorthand if can be used. The statement can be put on the same line as the if statement. 

syntax:
```Python
if <bool_expr>: <suite>
```

Example:
```Python
if (2 < 3): print(True)
```
# short hand if-else
This can be used to write the `if-else` statements in a single line where only one statement is needed in both the `if` and `else` blocks.

syntax:
```Python
<if_suite> if <bool_expr> else <else_suite>
```

Example:
```Python
print("if suite") if (2 > 3) else print("else suite")
```

```Python
print("if suite") if (2 < 3) else print("else suite")
```

