- Usually, a C program starts with the `main` [[functions|function]].
- The `main()` function is the entry point to a C/C++ program.
- The `main()` function in C is the starting point of program execution.
- `main()` is called when the application starts executing.
- Since C Language is a sequentially executed [procedural language](https://en.wikipedia.org/wiki/Procedural_programming), the statement or instructions written in the main function in C are executed sequentially in the order it is written.

Syntax:

```C
int main()
{
    // function body

    return 0;
}
```

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

