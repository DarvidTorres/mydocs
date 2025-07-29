- When a [[C/variables/variables|variable]] is created, a memory address is assigned to the variable. ^f4cfb8
- The memory address is the location of where the variable is stored on the computer.
- Every time a program is re-executed the address allocation changes.
- When we assign a [[C/data types/types#value range|value]] to the variable, it is stored in this memory address.
- To get a variable's address use the reference operator (`&`).
- The memory address is in hexadecimal form (0x..).
- To print memory addresses use the `%p` [[format specifiers|format specifier]].

Example:
```C
#include <stdio.h>

int main() {
    int myVar = 3;
    printf("%p", &myVar); // use & to get the address of myVar
    
    return (0);
}
```
