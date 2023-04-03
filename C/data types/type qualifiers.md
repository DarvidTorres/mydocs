A type qualifier is a [[tokens#Keywords|keyword]] that is applied to a type, resulting in a qualified type.

A type qualifier is used to refine the declaration of a variable, a function, and parameters, by specifying whether:
- The value of an object can be changed.
- The value of an object must always be read from memory rather than from a register.
- More than one pointer can access a modifiable memory address.

C supports:
- `const`
- `restrict`
- `volatile`
- `_Atomic`

# const

- `const` declares a [[variables|variable]] to be a [[tokens#constants|constant]] (unmodifiable variable).
- Prevents changes to defined variables.
- variables declared with `const` will default to $0$.

Example:

```C
#include <stdio.h>

int main() 
{
	const int a;
	printf("%d", a);
	
	return 0;
}
```

* Since `const` variables can't be modified, we must assign value at declaration or we'll get unmodifiable default value.

Example:

```c
#include <stdio.h>
int main() {
    const int a = 3;

	return (0);
}
```

- If we try to modify a `const` variable, the compiler will terminate with an error.

Example:

```C
#include <stdio.h>
int main()
{
    const int i = 5;
    i++;

	return (0);
}
```

It is considered good practice uppercase `const` variables. It is not required, but useful for code readability and common for C programmers:

```c
const int BIRTHYEAR = 1980;
```

# volatile

A volatile qualifier is used to declare a variable that can be changed at any point of time and explicitly, i.e., it always tells the compiler that the variable’s value may change at any time.
It will be useful for embedding programming in order to keep the updated value that can be changed from various interrupts.
To declare a volatile variable, the keyword ‘volatile’ is used.
In order to declare a volatile variable, include the keyword volatile before or after the data type.