
we can alter what address are stored in pointers (not only the value stored but the address itself):

```c
#include <stdio.h>
int main()
{
int a = 10, *p = &a;
printf("Address stored in p is %ls\n", p);
printf("Value at address p is %d\n", *p);
printf("size of integer is %ld bytes \n", sizeof(int)); // for `sizeof(type)` use `%ld` type
printf("Address p+1 is %ls\n", p+1);
printf("value at address p+1 is %d\n",*(p+1));
}
```

the `p+1` statement is not adding `1` byte to the address, but `1` type unit. For instance, if it's `int` it will add 4 units to address as `int` takes 4 bytes of memory.
