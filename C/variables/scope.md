- A scope is a region of a program where a defined variable can be accessed.
- A variable can be declared:
	- Inside a function or a block which is called local variables.
	- Outside of all functions which is called global variables.
	- In the definition of function parameters which are called formal parameters.

# local scope

Variables that are declared inside a function or block are called local variables. They can be used only by statements that are inside that function or block of code. Local variables are not known to functions outside their own.

The scope of a variable is the block of code in the entire program where the variable is declared, used, and can be modified.

Syntax:

```c
{
	/*BLOCK 1*/
    // contents of BLOCK 2 cannot be accessed here
}

{
	/*BLOCK 2*/
    // contents of BLOCK 1 cannot be accessed here
}
```

```c
{
	/*OUTER BLOCK*/
    
	{    /*INNER BLOCK*/
        //contents of the outer block just before the start of this block
        //CAN be accessed here
      }
    
       //contents of the inner block are NOT accessible here
 }
```

Example:

```C
#include <stdio.h>
 
int main () {

  /* local variable declaration */
  int a, b;
  int c;
 
  /* actual initialization */
  a = 10;
  b = 20;
  c = a + b;
 
  printf ("value of a = %d, b = %d and c = %d\n", a, b, c);
 
  return 0;
}
```

# global scope

Global variables are defined outside a function, usually on top of the program. Global variables hold their values throughout the lifetime of your program and they can be accessed inside any of the functions defined for the program.

A global variable can be accessed by any function. That is, a global variable is available for use throughout your entire program after its declaration.

Syntax:

```c
/*all global variables are declared here */

<function1>()
	{
    // all global variables can be accessed inside function1
    }
    
<function2>()
	{
    // all global variables can be accessed inside function2
    }
```

Example:

```C
#include <stdio.h>
 
/* global variable declaration */
int g;
 
int main () {

  /* local variable declaration */
  int a, b;
 
  /* actual initialization */
  a = 10;
  b = 20;
  g = a + b;
 
  printf ("value of a = %d, b = %d and g = %d\n", a, b, g);
 
  return 0;
}
```

A program can have same name for local and global variables but the value of local variable inside a function will take preference.

Example:

```C
#include <stdio.h>
 
/* global variable declaration */
int g = 20;
 
int main () {

  /* local variable declaration */
  int g = 10;
 
  printf ("value of g = %d\n",  g);
 
  return 0;
}
```