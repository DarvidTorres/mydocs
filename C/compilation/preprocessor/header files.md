A header file is a file that contains C [[prototypes|function declarations]], [[macros|macro]] definitions, and [[scope#global scope|global variables]], to be shared between several source files.

Including a header file produces the same results in C compilation as copying the header file into each source file that needs it. The header file eliminates the labor of finding and changing all the copies as well as the risk that a failure to find one copy will result in inconsistencies within a program.

By convention, header files are named with either a `.h` extension. However, there is no requirement that this is observed.

Example:

Let's say we have a file named `header.h` in our directory, which contains the following prototype: 

`char *test (void);`

another program (a `.c` file) might use that header as:

```c
#include "header.h"

int main () {
   puts (test ());
}
```

Which will then be read by the compiler as:

```c
char *test (void);

int main (void) {
   puts (test ());
}
```

 When a header file is included twice within a program, the compiler processes the contents of that header file twice which leads to an error in the program. To eliminate this error, [[conditional compilation|conditional preprocessor directives]] are used.

# \#include

C has some features as part of the language and some others as part of a [[standards#standard library|standard library]]. 

The `#include` directive works by directing the C preprocessor to scan the specified file as input before continuing with the rest of the current source file.

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

The preprocessor replaces the line `#include <stdio.h>` with the textual content of the file `stdio.h`, which declares the `printf()` function (among other things).

There are two types of header files:
- Standard / Pre-existing header files
- Non-Standard / User-defined header files

For this reason, header files can be invoked by the `#include` [[directives|directive]] using angle brackets or by using quotation marks.
- If the filename is enclosed within angle brackets (`< >`), the file is searched for in the standard compiler include paths.
	- `#include <file>` searches for a file named 'file' in a standard list of system directories.
- If the filename is enclosed within double quotes (`" "`), the search path is expanded to include the current source file directory.
	- `#include "file"` searches for a file named 'file' in the directory containing the current file.

C compilers and programming environments all have a facility that allows the programmer to define where include files can be found. 