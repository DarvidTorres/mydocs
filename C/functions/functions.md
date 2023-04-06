- Declarations are used to introduce the name of a function ([[tokens#Identifiers|identifier]]), its return type and the type (if any) of its arguments.
	- A declaration is equivalent to the function [[prototypes|prototype]].
- Definition is a declaration with the body of the function given too.

Function definition syntax:

```c
<type> <funName>() {
  // Body of the function  
}
```

We can pass arguments to a function, but we need to define the parameters. Parameters and return values must have a type. `void` indicates no return type.

```c
<type> <funName>(<type1> <par1>, <type2> <par2>) {  
  // code to be executed  
}
```

The simplest function of all is the empty function, which does nothing at all:

```C
void empty(void)
{
// do nothing
}
```

Use the identifier to invoke / call a function and pass parameters (if were declared):

Example:

```C
void empty(void) // define a function
{
// do nothing
}

int main()
{
    empty(); // call the function
    
    return (0);
}
```

Another example:

```c
#include <stdio.h>
int printchar(char a) // define function
{
    printf("%c", a);
}

int main()
{
    printchar('b'); // call function
    
    return (0);
}
```

We can declare a function (include the prototype), and later define it:

```C
#include <stdio.h>
int printchar(char a); // declare printchar

int printchar(char a) // define printchar
{
    printf("%c", a);
}

int main()
{
    printchar('b'); // call printchar
    
    return (0);
}
```

We can declare a function as many times in a source file:

```C
#include <stdio.h>
int printchar(char a); // declare function

int printchar(char a) // define function
{
    printf("%c", a);
}

int printchar(char a); // declare function again

int main()
{
    printchar('b');
    
    return (0);
}
```

But we cannot define a function more than once in a source file ([see why](https://www.linuxquestions.org/questions/programming-9/what-is-function-overriding-in-c-300383/)):

```C
#include <stdio.h>
int printchar(char a)
{
    printf("%c", a);
}

int printchar(char a)
{
    printf("%c", a);
}

int main()
{
    printchar('b');
    
    return (0);
}
```

# signature

A function signature defines:
- Arity (# of parameters)
- Parameter types

