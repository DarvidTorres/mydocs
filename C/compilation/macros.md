A macro is a fragment of code which has been given a name. Whenever the name is used, it is replaced by the contents of the macro.

You may define any valid identifier as a macro, even if it is a [[Overview#keywords|C keyword]]. The [[compilation#1. Preprocessor|preprocessor]] does not know anything about keywords.

# Object-like

An object-like macro is an identifier which will be replaced by a code fragment.

It is called object-like because it looks like a data object in code that uses it. They are most commonly used to give symbolic names to numeric constants.

You create macros with the `#define` directive. `#define` is followed by the name of the macro and then the token sequence it should be an abbreviation for, which is variously referred to as the macro’s body, expansion or replacement list.

Synaxis:

```C
#define <MACRO_NAME> <token>
```

By convention, macro names are written in uppercase.

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

Example:

```C
#include <stdio.h>

#define MY_MACRO 3

int main() {
    int a = MY_MACRO;
    printf("%d", a);
}
```



# function-like

To define a function-like macro, you use the same ‘#define’ directive, but you put a pair of parentheses immediately after the macro name.



- Function-like macros resemble function calls.


