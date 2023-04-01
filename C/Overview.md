All the code has to be inside a function.

The `main()` function is the entry point to a C/C++ program and is called when the application starts executing. 

You have to compile C files with a compiler (for instance gcc) to create an
executable file.

C is strongly associated with UNIX, as it was developed to write the UNIX operating system.

`#include <stdio.h>`: is a header file library that lets us work with input and output functions, such as `printf()`. Header files add functionality to C programs.

thing that always appear in a C program, is `main()`. This is called a function. Any code inside its curly brackets {} will be executed.

- Every C statement ends with a semicolon ;
- return 0 ends the main() function.

In C and C++ programs the `main` function is of type `int` and therefore it should return an integer value. The return value of the `main` function is considered the "Exit Status" of the application. On most operating systems returning 0 is a success status like saying "The program worked fine".

```c
#include <stdio.h>

int main() {
  printf("Hello World!");
  printf("I am learning C.");
  return 0;
}
```
There's no new line between outputs.

when you have only one char in the `printf()` the compiler turns it into a `putchar()`

```c
#include <stdio.h>
int main()
{
    puts("Geeksfor");
    puts("Geeks");
 
    getchar();
    return 0;
}
```

Program that prints exactly "Programming is like building a multilingual puzzle:

```C
#include <stdio.h>
int main(void)
{
puts("\"Programming is like building a multilingual puzzle");
return (0);
}
```

`puts` appends a new line to the end of output, while `fputs` and `printf` do not:

```C
/* Need to escape a new line */
#include<stdio.h>
int main(void)
{
printf("with proper grammar, but the outcome is a piece of art,\n");
return (0);
}
```

# keywords

The following are C keywords:

`auto`, `double`, `int`, `struct`, `break`, `else`, `long`, `switch`, `case`, `enum`, `register`, `typedef`, `char`, `extern`, `return`, `union`, `const`, `float`, `short`, `unsigned`, `continue`, `for`, `signed`, `void`, `default`, `goto`, `sizeof`, `volatile`, `do`, `if`, `static`, `while`, `const`, `signed`, `void` and `volatile`

# C standards

The C standards are documents that are intended to reduce variation in C language implementation across the different compilers. An “implementation” is basically the combination of the compiler, and the hardware platform. C standards are highly technical documents, are written for compiler implementers and they define the standard behavior a C implementation must follow.

There are a number of those standards, and a certain C implementation that abides by the standard is known as “Standard C” or “ISO C”. Complying with the standard doesn’t mean a certain implementation cannot add its own features, and most of them do (e.g. the GCC has extra features that can be accessed by defining the \_GNU\_SOURCE macro).

- C89: The first C standard, published by the American National Standards Institute (ANSI) in 1989, hence the name C89. You can check compiler support for ANSI C by checking for the definition of the __ANSI__ macro.
- C90: The C89 was adopted by the International Organization for Standardization (ISO) in 1990, and is known as C90.
- C95: Extension to C90, published in 1995. Added some features like digraphs and multibyte support. It also defined the __STDC_VERSION__ macro that can be tested to determine the version of ISO C a certain compiler supports.
- C99: Improvements added to C95 like C++-style single line comments, inline functions, plus addition of more headers.
- C11: published in 2011. Added some keywords (like _Generic) and a multi-threading API. Improved Unicode support.

# definition && declarations

- An identifier is a label (name) for a [[variables|variable]] or a [[functions|function]].
- A declaration introduces an identifier and describes its type.
- A declaration is what the [[compilation|compiler]] needs to accept references to that identifier.

- A definition is a declaration that provides all information about the identifiers it declares.
- A definition is what the linker needs in order to link references to those entities.