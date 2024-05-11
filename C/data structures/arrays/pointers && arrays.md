- An array name is a constant pointer to the first element of the array.
	- in the code `double balance[50];`,
		- `balance` is the name of an array of size 50, but `balance` is also a pointer to `&balance[0]`, which is the address of the first element of the array `balance`.

Example:

```C
#include <stdio.h>
 
int main()
{
    int myNumbers[4] = {25, 50, 75, 100};

    // Get the memory address of the myNumbers array
    printf("%p\n", myNumbers);
    
    // Get the memory address of the first array element
    printf("%p\n", &myNumbers[0]);
}
```

Since the name of the array is a pointer itself, we can use the `*` operator on it:

```C
#include <stdio.h>
 
int main()
{
    int myNumbers[4] = {25, 50, 75, 100};

    // Get the value of the first element in myNumbers
    printf("%d", *myNumbers);
}
```

To access the rest of the elements in myNumbers, you can increment the pointer/array (+1, +2, etc):

```C
int myNumbers[4] = {25, 50, 75, 100};

// Get the value of the second element in myNumbers
printf("%d\n", *(myNumbers + 1));

// Get the value of the third element in myNumbers
printf("%d", *(myNumbers + 2));

// and so on..
```
