# Booleans

`bool` type

```c
bool isProgrammingFun = true;
bool isFishTasty = false;
```

# switch

The switch statement selects one of many code blocks to be executed:

```c
switch(expression) {
  case x:
    // code block
    break;
  case y:
    // code block
    break;
  default: /* optional */
    // code block
}
```

1. The switch expression is evaluated once
2. The value of the expression is compared with the values of each case
3. If there is a match, the associated block of code is executed
4. The break statement breaks out of the switch block and stops the execution
5. The default statement is *optional*, and specifies some code to run if there is no case match

The default keyword must be used as the last statement in the switch, and it does not need a break.

Example 

```c
int day = 4;

switch (day) {
  case 6:
    printf("Today is Saturday");
    break;
  case 7:
    printf("Today is Sunday");
    break;
  default:
    printf("Looking forward to the Weekend");
}

// Outputs "Looking forward to the Weekend"
```

# while

```C
while (_condition_) {  
  _// code block to be executed_  
}
```

The code in the loop will run, over and over again, as long as a variable (`i`) is less than 5:

```C
#include <stdio.h>

int main() {
	int i = 0;  
  
	while (i < 5) {  
	  printf("%d\n", i);  
	  i++;  
	}

	return 0;
}
```

## Do/While

`do/while` will execute the code block once, before checking if the condition is true, then it will repeat the loop as long as the condition is true.

```C
do {  
  _// code block to be executed_}  
while (_condition_);
```

The loop will always be executed at least once, even if the condition is false, because the code block is executed before the condition is tested:

```C
int main() {
	int i = 0;

	do {
		print("%d\n", i);
		i++;
	}
	while (i < 5);

	return 0;
}
```


# for

```c
for (statement1; statement2; statement3) {  
  // code block to be executed_  
}
```

`statement1` is executed (one time) before the execution of the code block.
`statement2` defines the condition for executing the code block.
`statement3` is executed (every time) after the code block has been executed.

# nested loops

Example of a nested while that prints

2 2 2 
2 2 2 
2 2 2 
2 2 2 
2 2 2 

```c
#include <stdio.h>

main()
{
int i = 0, j = 0;

while(i<5) {
	while(j<3)
		{
		printf("2 ");
		j++;
		}
	
	printf("\n");
	i++;
			}

return (0);
}
```