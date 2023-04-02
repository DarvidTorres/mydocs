- Conditional [[compilation]] implies that source code is compiled if certain condition(s) hold true.
- Directives control the selective/conditional compilation of portions of the program code.
- Six directives are available to control conditional compilation.

# \#if,  \#else and   \#elif

- `#if` is a preprocessor directive in C to define conditional compilation.
- `#if` can be used just like an [[if else|if condition statement]]; it impacts the compilation process and the executable that is created.
- `#if` checks whether the given condition is true (nonzero).
- Each `#if` directive in a source file must be matched by a closing `#endif` directive.

Syntax:

```C
#if <condition>
  <code statements>
#endif
```

- The `#if` directive, with the `#elif`, `#else`, and `#endif` directives, controls compilation of portions of a source file.
- Any number of `#elif` directives can appear between the `#if` and `#endif` directives, but at most one `#else` directive is allowed.
- The `#else` directive, if present, must be the last directive before `#endif`.

Syntax:

```C
#if <condition>
  <code statements>
#elif
  <code statements>
#else
  <code statements>
#endif
```

Example (using a [[macros|macro]] definition):

```C
#include <stdio.h>

#define myMacro 1

int main()
{
   #if myMacro != 0
       printf("myMacro is defined to a non-zero value.");
   #endif
}
```

Example (using ):

```C
#include <stdio.h>

#define myMacro

int main() 
{
	#if defined myMacro
	    printf("%d", myMacro);
	#endif
	return 0;
}
```





 
This construct is called wrapper `#ifndef`.

```c
#ifndef HEADER_FILE_NAME
#define HEADER_FILE_NAME

   /* the entire header file */

#endif
```

When the header is included again, the conditional will become false, because `HEADER_FILE_NAME` is defined. The preprocessor will skip over the entire contents of the file and the compiler will not see it twice.




# \#ifdef

- The `#ifdef` directive checks for the existence of [[macros|macro]] definitions.
- `#ifdef` allows the inclusion of source code if the provided macro identifier has been defined.
- If the identifier specified is defined as a macro, the lines of code that immediately follow the condition are passed on to the compiler.
- The preprocessor determines if the provided macro exists before including the subsequent code in the compilation process.
- An identifier must follow the `#ifndef` keyword.
- The `#ifdef` directive must be closed by an `#endif` directive.

Syntax:

```C
#ifdef <macro_definition>
```



