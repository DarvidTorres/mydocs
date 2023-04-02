- Conditional [[compilation]] implies that source code is compiled if certain condition(s) hold true.
- Directives control the selective/conditional compilation of portions of the program code.

# \#if,  \#else and  \#elif

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

In contrast, if an identifier was created using the #[[macros#define|define]] directive but was not assigned a value, the compiler doesn't assigned a value.

Example

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
- While `#if` evaluates any (valid) [[logical operators|logical condition]], `#ifdef` evaluates whether an identifier has been defined.

Example:

```C
#include <stdio.h>

#define FOO 0

int main() {
    
    #ifdef FOO
    printf("This will print\n");
    #endif

	#if defined FOO
	printf("This will also print\n");
	#endif
    
    #if FOO
    printf("This won't print\n");
    #endif
    
    return (0);
}
```

Other than evaluate whether an identifier has been defined, we can't evaluate logical conditions with `#ifdef`; if we try to do so, the compiler ends with a warning and we might get an unexpected result.

Example:

```C
#include <stdio.h>

#define FOO 0

int main() {
    
    #ifdef FOO && BAR
    printf("This will print but we get a warning\n");
    #endif
    
    #if defined(FOO) || defined(BAR)
    printf("This will print without warnings");
    #endif
    
    return (0);
}
```

# \#ifndef

- The `#ifdef` directive is equivalent to `#if !defined`.
- While `#if` evaluates any (valid) [[logical operators|logical condition]], `#ifndef` evaluates whether an identifier has not been defined.

```C
#include <stdio.h>

int main() {
    
    #ifndef FOO
    printf("This will print\n");
    #endif

	#if !defined FOO
	printf("This will also print\n");
	#endif
    
    #if FOO
    printf("This won't print\n");
    #endif
    
    return (0);
}
```

Other than evaluate whether an identifier has not been defined, we can't evaluate logical conditions with `#ifdef`; if we try to do so, the compiler ends with a warning and we might get an unexpected result.

```C
#include <stdio.h>

int main() {
    
    #ifndef FOO || BAR
    printf("This will print but we get a warning\n");
    #endif
    
    #if !defined(FOO) && !defined(BAR)
    printf("This will print without warnings");
    #endif
    
    return (0);
}
```

# \#undef

- The `#undef` directive removes the current definition of identifier.
- `#undef` can take an identifier that has no previous definition. This ensures that the identifier is undefined.

Syntax:

```C
#undef <IDENTIFIER>
```

Example:

```C
#include <stdio.h>

#define FOO 0

int main() {
    #ifdef FOO
    printf("This will print\n");
    #endif
    
    #undef FOO
    
    #ifndef FOO
    printf("This will also print\n");
    #endif
    
    return (0);
}
```