An array is a collection of items stored at contiguous [[memory]] locations.

![](https://i.imgur.com/Zdtx6Ug.png)

`type arrayName[ arraySize ];`: declare a single-dimension array

`double balance[5] = {1000.0, 2.0, 3.4, 7.0, 50.0};` declare a `double` array called `balance` of dimension $5$, with elements from the set `{1000.0, 2.0, 3.4, 7.0, 50.0}`.

`A[5]`: create an array that contains 5 integers that are stored next to each other in memory, to access each integer we can get the value by `A[0]` to get the value of the first integer in the array, and `A[4]` to get the last integer in the array.

If you omit the size of the array, an array just big enough to hold the initialization is created. Therefore, if you write  `double balance[] = {1000.0, 2.0, 3.4, 7.0, 50.0};` the compiler understands the array size

- `&A[i]` or `(A+i)`: Address of integer `i` in array `A`.
- `A[i]` or `*(A+i)`: Value of integer `i` in array `A`.

We can run loops over arrays:

```c
#include <stdio.h>
int main()
{
int A[] = {2,4,5,8,1};
int i;
for (int i = 0; i < 5; i++)
{
printf("Address = %ls\n", &A[i]);
printf("Address = %ls\n", A+i);
printf("Value = %d\n", A[i]);
printf("Value = %d\n", *(A+i));
}
}
```

Example:

```C
int myNumbers[4] = {25, 50, 75, 100};
int i;

for (i = 0; i < 4; i++) {
  printf("%d\n", myNumbers[i]);
}
```

Instead of printing the value of each array element, let's print the memory address of each array element:

```C
int myNumbers[4] = {25, 50, 75, 100};
int i;

for (i = 0; i < 4; i++) {
  printf("%p\n", &myNumbers[i]);
}
```

