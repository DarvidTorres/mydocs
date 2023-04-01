A header file is a file with extension `.h` which contains C function declarations and [[macros|macro]] definitions to be shared between several source files.

Statements like `#include <stdio.h>` and `#include <string.h>` include prototypes without implementation, in that way the compiler can make the proper assumptions.

There are two types of header files: the files that the programmer writes and the files that comes with your compiler.

- The `#include` directive works by directing the C preprocessor to scan the specified file as input before continuing with the rest of the current source file.
- `#include <file>` searches for a file named 'file' in a standard list of system directories.
- `#include "file"` searches for a file named 'file' in the directory containing the current file.

Basically headers act as placeholders for prototypes.

Example:

Let's say we have a file named `header.h` in our directory, which contains the following prototype: 

`char *test (void);`

another program might use that header as:

```c
int x;
#include "header.h"

int main (void) {
   puts (test ());
}
```

Which will then be read by the compiler as:

```c
int x;
char *test (void);

int main (void) {
   puts (test ());
}
```

 When a header file is included twice within a program, the compiler processes the contents of that header file twice which leads to an error in the program. To eliminate this error, **conditional preprocessor directives** are used.
 
This construct is called wrapper `#ifndef`.

```c
#ifndef HEADER_FILE_NAME
#define HEADER_FILE_NAME

   /* the entire header file */

#endif
```

When the header is included again, the conditional will become false, because `HEADER_FILE_NAME` is defined. The preprocessor will skip over the entire contents of the file and the compiler will not see it twice.