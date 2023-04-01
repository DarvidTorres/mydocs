A macro is a fragment of code which has been given a name. Whenever the name is used, it is replaced by the contents of the macro.

You may define any valid identifier as a macro, even if it is a [[Overview#keywords|C keyword]]. The [[preprocessor|preprocessor]] does not know anything about keywords.

By convention, macro names are written in uppercase.

# Object-like

An object-like macro is an identifier which will be replaced by a code fragment.

It is called object-like because it looks like a data object in code that uses it. They are most commonly used to give symbolic names to numeric constants.

You create macros with the `#define` directive. `#define` is followed by the name of the macro and then the token sequence it should be an abbreviation for, which is variously referred to as the macro’s body, expansion or replacement list.

Synaxis:

```C
#define <MACRO_NAME> <token>
```

Examples:

```C
#define MAX 100
#define MIN 1
#define GRAVITY 9.8
#define NAME "Scaler"
#define TRUE 1
#define FALSE 0
```

The C preprocessor will recognize and expand macros.

The following object-like definition causes the preprocessor to replace all subsequent instances of the identifier `COUNT` with the constant `1000` : `#define COUNT 1000`. If the statement `int arry[COUNT];` appears after this definition and in the same file as the definition, the preprocessor would change the statement to  `int arry[1000];` in the output of the preprocessor.

Example:

```C
#include <stdio.h>

#define MY_MACRO 3

void main() {
    int a = MY_MACRO;
    printf("%d", a);
}
```

# function-like

To define a function-like macro, use the same `#define` directive, and put parentheses immediately (no space in between) after the macro name.

Syntax:

```C
#define <MACRO_NAME>() <token>
```

Function-like macros can take arguments, like true functions.

To define a macro that uses arguments, insert parameters between the pair of parentheses in the macro definition that make the macro function-like. The parameters must be valid C identifiers, separated by commas and optionally whitespace.

Example:

```C
#include <stdio.h>

#define SQR(c) ((c) * (c))

void main() {
    int a = SQR(3 + 1);
    printf("%d", a);
}
```

A common error would be to write:

```C
#include <stdio.h>

#define SQR(c) c*c

void main() {
    int a = SQR(3 + 1);
    printf("%d", a);
}
```

As the preprocessor changes the code: `SQRT(3 + 1)` into `3+1*3+1`, and thus, not yielding the desired result.

The above, is an example of [macro pitfalls](https://gcc.gnu.org/onlinedocs/cpp/Macro-Pitfalls.html#Macro-Pitfalls).

# chain-like macros

We can use macros inside macro definitions.

Example:

```C
#include <stdio.h>
#define PI 3.14 //object like macro
#define Area(r) (PI*(r*r)) // function like macro

void main()
{
    float radius = 2.5; // declaration and initialization of radius
    float area = Area(radius); // declaring and assigning the value to area
    printf("Area of circle is %f\n", area); // Printing the area of circle
}
```

# Predefined Macros

- Some object-like macros are [predefined](https://gcc.gnu.org/onlinedocs/cpp/Predefined-Macros.html#Predefined-Macros); use them without supplying their definitions.
- Predefined macros aren't modifiable.

Examples:
| Macro      | Feature                                                         |
| ---------- | ----------------------------------------------------------------|
| \__LINE\__ | Contains the current line number on which this macro is used.       |
| \__FILE\__ | Contains the name of the file where the current program is present. |
| \__DATE\__ | Contains the current date in MMM DD YYYY format.                    |
| \__TIME\__ | Contains the current time in HH:MM format.                          |
| \__STDC\__ | Is defined as 1 when there is a successful compilation.             |

```C
#include <stdio.h>

void main()
{
    printf("This is line no.: %d\n", __LINE__);
    printf("Name of this file: %s\n", __FILE__);
    printf("Current Date: %s\n", __DATE__);
    printf("Current Time: %s\n", __TIME__);
    printf("Compilation success: %d\n", __STDC__);
}
```




