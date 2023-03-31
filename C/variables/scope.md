# local scope

The scope of a variable is the block of code in the entire program where the variable is declared, used, and can be modified.

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

# global scope

```c
/*all global variables are declared here */

function1()
	{
    // all global variables can be accessed inside function1
    }
    
function2()
	{
    // all global variables can be accessed inside function2
    }
```

