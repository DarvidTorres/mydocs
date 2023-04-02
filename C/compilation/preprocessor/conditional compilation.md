- Directives are instructions to the preprocessor which allow additional actions to be taken on the source code before it is compiled into object code.
- Directives are not part of the C language itself.
- Directives begin with the has (`#`) symbol.
- Directives can be nested.
- Six directives are available to control conditional compilation.

# conditional compilation

- Conditional [[compilation]] implies that source code is compiled if certain condition(s) hold true.
- Directives control the selective/conditional compilation of portions of the program code.

# \#include

C has some features as part of the language and some others as part of a [[standards#standard library|standard library]]. The `#include` directive Inserts a particular header from another file.

It includes another C file into the current file at the location of the `#include` statement prior to compiling the source code.

Example:

```C
#include <stdio.h>

int main(void)
{
    printf("Hello, World!\n");
    return 0;
}
```

The preprocessor replaces the line `#include <stdio.h>` with the textual content of the file `stdio.h`, which declares the `printf()` function among other things.

# \#define



# \#if

Syntax:

```C
#if constant-expression newline
```





