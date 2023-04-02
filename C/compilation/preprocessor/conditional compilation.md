- Conditional [[compilation]] implies that source code is compiled if certain condition(s) hold true.
- Directives control the selective/conditional compilation of portions of the program code.
- Six directives are available to control conditional compilation.

# \#if,   \#else and   \#elif

The `#if` directive, with the `#elif`, `#else`, and `#endif` directives, controls compilation of portions of a source file.

- `#if` checks whether the constant-expression is true (nonzero).
- Each `#if` directive in a source file must be matched by a closing `#endif` directive.
- Any number of `#elif` directives can appear between the `#if` and `#endif` directives, but at most one `#else` directive is allowed.
- The `#else` directive, if present, must be the last directive before `#endif`.

Syntax:

```C
#if <constant-expression>
```





 
This construct is called wrapper `#ifndef`.

```c
#ifndef HEADER_FILE_NAME
#define HEADER_FILE_NAME

   /* the entire header file */

#endif
```

When the header is included again, the conditional will become false, because `HEADER_FILE_NAME` is defined. The preprocessor will skip over the entire contents of the file and the compiler will not see it twice.


