- A function is a group of statements that together perform a task.
- Every C program has at least one function, which is [[main function|main()]].
- A function can also be referred as a method, a sub-routine or a procedure.

# declaration

- A function declaration states the name of a function ([[tokens#Identifiers|identifier]]), its return type and the type of its arguments (if any).
	- A declaration is equivalent to the function [[prototypes|prototype]].

Function declaration syntax:

```c
<type> <funName>([parameter list]);
```

Parameter names are not important in function declaration only their type is required. 

Example:

```C
int max(int, int);
```

Function declaration is required when you define a function in one source file and you call that function in another file.

# definition

- A function definition is a declaration with the body of the function given too.
- A function definition in C programming consists of a function header and a function body.

Return Type − A function may return a value. The return_type is the data type of the value the function returns. Some functions perform the desired operations without returning a value. In this case, the return_type is the keyword void.

Function Name − This is the actual name of the function. The function name and the parameter list together constitute the function signature.

Parameters − A parameter is like a placeholder. When a function is invoked, you pass a value to the parameter. This value is referred to as actual parameter or argument. The parameter list refers to the type, order, and number of the parameters of a function. Parameters are optional; that is, a function may contain no parameters.

Function Body − The function body contains a collection of statements that define what the function does.

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

# function call

While creating a C function, you give a definition of what the function has to do. To use a function, you will have to call that function to perform the defined task.

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
int printchar(char); // declare printchar

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

