## Function prototype / signature

A function prototype declares a [[functions|function]] but does not define it.

```c
<rtrnType> functionName(<type1> <arg1>, <type2> <arg2>, ...);
```

In a prototype, parameter names are optional, so `void Sum( int a, int b );` and `void Sum( int, int );` are valid prototypes.

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