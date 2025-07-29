- Pointers are [[C/variables/variables]] that store a variable [[C/memory/address]].
- Pointers have a [[C/data types/types|type]].
- Pointer type must match the variable type it *points* to.
- In 64-bit data models, pointer size are always 8 bytes (64 bits).

Pointer declaration syntax:
```C
<varType> <varName>; // variable declaration
<varType> * <ptrName> = &<varName>; // pointer declaration
```

Example:

```C
#include <stdio.h>

int main() {
    int myVar = 3;
    int * myPtr = &myVar;
    printf("Address stored in myPtr is %p", myPtr); 
    
    return (0);
}
```

As pointers are variables, we can declare a pointer without assigning the value, and assign the value later.

Example:

```C
#include <stdio.h>

int main() {
    int myVar; // declare variable
    int * myPtr; // declare pointer
    myPtr = &myVar; // define pointer
    printf("Address stored in myPtr is %p", myPtr);
    
    return (0);
}
```

Note that we don't need to define the variable the pointer *points to*, since the pointer itself only stores the variable's address (not its value).

- Since pointers are variables, they (themselves) have an address.
- Since pointers have an address, they can store their own address.

Example:

```C
#include <stdio.h>

int main() {
    void * my_self; // pointer declaration
    my_self = &my_self; // pointer definition
    printf("Address stored in my_self is %p", my_self);
    
    return (0);
}
```

Though pointers can point to themselves, it is practically useless, as we can get a pointer's [[C/memory/address]] by using the reference operator `&`. 

Example:
```C
#include <stdio.h>

int main() {
    void * my_self;
    printf("Address stored in my_self is %p", &my_self);
    
    return (0);
}
```