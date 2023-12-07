A match statement takes an expression and compares its value to successive patterns given as one or more case blocks.
- Only the first pattern that matches gets executed.
- It is also possible to extract components (sequence elements or object attributes) from the value into variables.

syntax:
```Python
match <identifier>:
   case 'pattern 1' : <suite 0>
   case 'pattern 2' : <suite 1>
   ...
   case 'pattern n' : <suite n>
```
