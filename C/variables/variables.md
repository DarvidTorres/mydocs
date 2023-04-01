- Variables are names given to [[memory]] locations for storing [[types#value range|data values]].
- Name variables are called identifiers.
- Variables have [[types|type]].

To declare a variable assign type and name:

```C
<type> <varName>;
```

Example:

```C
#include <stdio.h>

int main() {
    int myVar; // variable declaration
    
    return (0);
}
```

To assign (or store) a [[types#value range|value]] in a variable, use the `=` operator; we call this operation variable definition or initialization:

```C
<varName> = <value>;
```

Examples:

 - Declare a variable without assigning the value, and assign the value later.

```C
int main() {
    int a;
    a = 3;

	return (0);
}
```

- Declare a variable and assign value at once.

```C
int main() {
    int a = 3;

	return (0);
}
```

- To declare multiple variables at once use comma separators.
	- To declare multiple variables at once they must match [[types|type]].
	- We can:
		- Declare multiple variables, and assign the value later.
		- Declare multiple variables and assign value at once.

```C
#include <stdio.h>

int main() {
	int a, b;
	a = 3;
	b = 4;
	
	int x = 5, y = 6, z = 50;
	
    return 0;
}
```

To display the value of variables in the terminal use [[format specifiers]].

Example:

```C
#include <stdio.h>

int main() {
    int x, y, z;
	x = y = z = 50;
	printf("%d", x + y + z);
    
    return (0);
}
```