syntax
```Python
range(<start>, <stop>[, <step>])
```
Note: the arguments to the range constructor **must be integers**.
- If the `step` argument is omitted, it defaults to 1.
	- If `step` is 0, ValueError is raised.
- If the `start` argument is omitted, it defaults to 0.
- The range will stop a `step` unit before `<stop>`.

Example:
```Python
print(*range(3), sep = ', ')
```
