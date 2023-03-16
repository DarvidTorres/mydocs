- **Declaration**: the function's name, return type, and parameters (if any).
- **Definition**: the body of the function (code to be executed).

```c
rtrn_type name_fn() {  
  // code to be executed  
}
```

Example:

```c
// Create a function  
void myFunction() {  
  printf("I just got executed!");  
}  
  
int main() {  
  myFunction(); // call the function  
  return 0;  
}  
  
// Outputs "I just got executed!"
```

Parameters and return values must have a type. `void` indicates no return type.

We can pass arguments to a function, but we need to define the parameters:

```c
rtrnType functionName(type holder1, type holder3) {  
  // code to be executed  
}
```

Example:

```c
/* function returning the max between two numbers */
int max(int num1, int num2) {

   /* local variable declaration */
   int result;
 
   if (num1 > num2)
      result = num1;
   else
      result = num2;
 
   return result; 
}
```

## Function prototype / signature

The function prototype specifies the input/output interlace to the function. Function's name, parameters and return type but not body, prior to the function's actual declaration.

```c
returnType functionName(type1 argument1, type2 argument2, ...);
```

 You place function prototypes at the beginning or anywhere in a program.

Many compilers do not check for parameter matching either in type or count (how many arguments and which types were passed) which could lead to unintended effects. Defining prototypes prior to invoke a function prevents the compiler from running if types and counts of all parameter do not match.

```c
#include <stdio.h>
int add (int,int); /* function prototype for add */

void main()
{
    printf("%d\n",add(3));
}

int add(int i, int j)
{
    return i+j;
}
```

In the example above the prototype causes the compiler to flag an error on the **printf** statement (because of parameter count).

If one doesn’t specify the function prototype, the behavior is specific to the C standard (either C90 or C99) that the compilers implement. Up to the C90 standard, C compilers assumed the return type of the omitted function prototype as int. And this assumption at the compiler side may lead to unspecified program behavior.

# examples

`isupper`
 