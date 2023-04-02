- Conditional [[compilation]] implies that source code is compiled if certain condition(s) hold true.
- Directives control the selective/conditional compilation of portions of the program code.
- Six directives are available to control conditional compilation.

# \#if

Syntax:

```C
#if constant-expression newline
```





 
This construct is called wrapper `#ifndef`.

```c
#ifndef HEADER_FILE_NAME
#define HEADER_FILE_NAME

   /* the entire header file */

#endif
```

When the header is included again, the conditional will become false, because `HEADER_FILE_NAME` is defined. The preprocessor will skip over the entire contents of the file and the compiler will not see it twice.


