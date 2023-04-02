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

If an identifier used in the expression is not currently defined, the compiler treats the identifier as though it were the constant zero (`FALSE`).

Example:

```C
#include <stdio.h>

int main() 
{
	#if A
	    printf("Hello World!");
	#endif
	
	return 0;
}
```

All conditions involving variables or other expressions that cannot be resolved in [[compilation|compile time]] will evaluate to false.

Example:

```C
#include <stdio.h>

int main() 
{
    int i = 1;
    
	#if i == 1  
	    printf("Hello World!");
	#endif
	
	return 0;
}
```

# \#ifdef

- The `#ifdef` directive is equivalent to `#if defined`.
- While `#if` evaluates a [[logical operators|logical condition]], `ifdef` evaluates whether an identifier has been defined.

Example:

```C
#include <stdio.h>

#define FOO 0

int main() {
    
    #ifdef FOO
    printf("This will compile\n");
    #endif
    
    #if FOO
    printf("This will not compile\n");
    #endif
    
    return (0);
}
```

Example:

While








