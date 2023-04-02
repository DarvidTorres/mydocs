- Conditional [[compilation]] implies that source code is compiled if certain condition(s) hold true.
- Directives control the selective/conditional compilation of portions of the program code.
- Six directives are available to control conditional compilation.

# \#if,  \#else and   \#elif

- `#if` is a preprocessor directive in C to define conditional compilation.
- `#if` impacts the compilation process and the executable that is created.
- `#if` can be used just like an [[if else|if condition statement]].
- `#if` checks whether the given condition is true (nonzero).
- The `#if` directive must be matched by a closing `#endif` directive.

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

Example (using a [[macros#define definition|macro]] definition):

```C
#include <stdio.h>

#define myMacro -1

int main() 
{
	#if myMacro % 2 == 0
	    printf("even");
	#elif myMacro % 2 == 1 
	    printf("odd");
	#else
	    printf("none");
	#endif
	return 0;
}
```

Example (using the [[macros#defined|defined operator]]):

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

If an identifier used in the expression is not currently defined, the compiler treats the identifier as though it were the constant zero.

Example:

```C
#include <stdio.h>

int main() 
{
	#if defined A
	    printf("Defined");
	#else
	    printf("Not defined");
	#endif
	return 0;
}
```

All conditions involving variables or other expressions that cannot be resolved in [[Overview#compile vs run time|compile time]] will evaluate to false.

```C
#include <stdio.h>

int main() 
{
    int i = 1;
    
	#if i == 1  
	    printf("No output");
	#endif
	return 0;
}
```

As [[directives]] can be nested, the condition in an `#if` directive is subject to text replacement and can contain references to [[Overview#definition and declarations|identifiers]] defined in previous `#define` directives. The replacement occurs before the expression is evaluated.

# \#ifdef

- The `#ifdef` directive checks for the existence of [[macros|macro]] definitions.
- If the identifier specified is defined as a macro, the lines of code that immediately follow the condition are passed on to the compiler.
- The `#ifdef` directive must be matched by a closing `#endif` directive.

 
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



