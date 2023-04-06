The C standards are documents that are intended to reduce variation in C language implementation across the different compilers. An “implementation” is basically the combination of the compiler, and the hardware platform. C standards are highly technical documents, are written for compiler implementers and they define the standard behavior a C implementation must follow.

There are a number of those standards, and a certain C implementation that abides by the standard is known as “Standard C” or “ISO C”. Complying with the standard doesn’t mean a certain implementation cannot add its own features, and most of them do (e.g. the GCC has extra features that can be accessed by defining the \_GNU\_SOURCE macro).

- C89: The first C standard, published by the American National Standards Institute (ANSI) in 1989, hence the name C89. You can check compiler support for ANSI C by checking for the definition of the \_\_ANSI\_\_ macro.
- C90: The C89 was adopted by the International Organization for Standardization (ISO) in 1990, and is known as C90.
- C95: Extension to C90, published in 1995. Added some features like digraphs and multibyte support. It also defined the \_\_STDC_VERSION\_\_ macro that can be tested to determine the version of ISO C a certain compiler supports.
- C99: Improvements added to C95 like C++-style single line comments, inline functions, plus addition of more headers.
- C11: published in 2011. Added some keywords (like _Generic) and a multi-threading API. Improved Unicode support.

# standard library

A library in C is a collection of [[header files]], exposed for use by other programs.

A standard library is a repository of code that is available alongside every standard-conformant C compiler. When the C compiler compiles your program it usually also links it with the standard C library.

The (ANSI) [standard library](https://en.wikibooks.org/wiki/C_Programming/Standard_libraries) of 24 C [[header files]] which can be included into a programmer's project with a single [[conditional compilation|directive]]. Each header file contains one or more function declarations, data type definitions and [[macros]].

Examples:
| Header file | Description                                                       | 
| ----------- | ----------------------------------------------------------------- |
| stdio.h     | Input/Output functions                                            |
| conio.h     | Console Input/Output functions                                    |
| stdlib.h    | General utility functions                                         |
| math.h      | Mathematics functions                                             |
| string.h    | String functions                                                  |
| ctype.h     | Character handling functions                                      |
| time.h      | Date and time functions                                           |
| float.h     | Limits of float types                                             |
| limits.h    | Size of basic types                                               |
| wctype.h    | Functions to determine the type contained in wide character data. |

```C
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <math.h>

int main() {
   char s1[20] = "53875";
   char s2[10] = "Hello";
   char s3[10] = "World";
   int res;

   res = pow(8, 4);
   printf("Using math.h, The value is : %d\n", res);

   long int a = atol(s1);
   printf("Using stdlib.h, the string to long int : %ld\n", a);
   
   strcpy(s2, s3);
   printf("Using string.h, the strings s2 and s3 : %s\t%s\n", s2, s3 );

   return 0;
}
```

# GNU

The GNU C Library, also known as `glibc`, is the [GNU Project's](https://www.gnu.org/software/libc/) implementation of the C Standard Library. Not all standard C functions are found in `glibc`: most mathematical functions are actually implemented in `libm`, a separate library.

As of today `glibc` is the most widely used C library on Linux.

# objects

In C programs there are two distinct types of things: things used to hold values and things that are functions. Instead of having to refer to them jointly with a clumsy phrase that maintains the distinction, we think that it's useful to call them both loosely ‘objects’. We do quite a lot of that later, because it's often the case that they follow more or less the same rules. Beware though, that this isn't quite what the Standard uses the term to mean. In the Standard, an ‘object’ is explicitly a region of allocated storage that is used to represent a value and a function is something different; this leads to the Standard often having to say ‘… functions and objects …’. Because we don't think that it leads to too much confusion and does improve the readability of the text in most cases, we will continue to use our looser interpretation of object to include functions and we will explicitly use the terms ‘data objects’ and ‘functions’ when the distinction is appropriate.