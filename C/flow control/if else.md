- Use if to specify a block of code to be executed, if a specified condition is true
- Use else to specify a block of code to be executed, if the same condition is false
- Use else if to specify a new condition to test, if the first condition is false

```c
if (condition) {
  // block of code to be executed if the condition is true
}
```

Example

```c
if (20 > 18) {
  printf("20 is greater than 18");
}
```

Using else:

```c

if (condition) {
  // block of code to be executed if the condition is true
} else {
  // block of code to be executed if the condition is false
}
```

Example

```c

int time = 20;
if (time < 18) {
  printf("Good day.");
} else {
  printf("Good evening.");
}
// Outputs "Good evening."
```

Using else if

```c
if (condition1) {
  // block of code to be executed if condition1 is true
} else if (condition2) {
  // block of code to be executed if the condition1 is false and condition2 is true
} else {
  // block of code to be executed if the condition1 is false and condition2 is false
}
```

Example

```c
int time = 22;
if (time < 10) {
  printf("Good morning.");
} else if (time < 20) {
  printf("Good day.");
} else {
  printf("Good evening.");
}
// Outputs "Good evening."
```

# Ternary or Conditional operator

- 3-ary if else statement

Syntax:

```C
<condition> ? <value_if_true> : <value_if_false>
```

The statement evaluates to `<value_if_true>` if condition is met, and `<value_if_false>` otherwise.

Example:

```c
#include <stdio.h>

int main() {

    int a = 2;
    if (a < 3) {
      printf("True if else.\n");
    } else {
      printf("False if else.\n");
    }
    
    /* Does the same as: */
    
    (a < 3) ? printf("True conditional op.\n") : printf("False conditional op.\n");
   
   return (0);
}
```
