C provides several standard integer types:. This table defines the minimum ranges allowed for these integer types.

>An implementation is free to define these types to hold greater ranges than the ones given here.

| Type               | Minimum Value        | Maximum Value        |
| ------------------ | -------------------- | -------------------- |
| signed char        | -127                 | 127                  |
| unsigned char      | 0                    | 255                  |
| short              | -32767               | 32767                |
| unsigned short     | 0                    | 65535                |
| int                | -32767               | 32767                |
| unsigned int       | 0                    | 65535                |
| long               | -2147483647          | 2147483647           |
| unsigned long      | 0                    | 4294967295           |
| signed long long   | -9223372036854775807 | 9223372036854775807  |
| unsigned long long | 0                    | 18446744073709551615 |

If you want to know the actual minimum and maximum values an implementation uses they are defined in the `limits.h` [[headers|header file]]. It defines various constants like SCHAR_MIN, SCHAR_MAX, etc. that give the values for this implementation of C. The following example shows the limits of this implementation:

```C
#include <stdio.h>
    #include <limits.h>
 
   void main()
   {
          printf("Signed char minimum value: %d\n", SCHAR_MIN );
          printf("Signed char maximum value: %d\n", SCHAR_MAX );
          printf("Unsigned char minimum value: %d\n", 0 );
          printf("Unsigned char maximum value: %d\n", UCHAR_MAX );
          printf("Char minimum value: %d\n", CHAR_MIN );
          printf("Char maximum value: %d\n", CHAR_MAX );
          printf("Signed short minimum value: %d\n", SHRT_MIN );
          printf("Signed short maximum value: %d\n", SHRT_MAX );
          printf("Unsigned short minimum value: %d\n", 0 );
          printf("Unsigned short maximum value: %d\n", USHRT_MAX );
          printf("Signed int minimum value: %d\n", INT_MIN );
          printf("Signed int maximum value: %d\n", INT_MAX );
          printf("Unsigned int minimum value: %u\n", 0 );
          printf("Unsigned int maximum value: %u\n", UINT_MAX );
          printf("Signed long minimum value: %ld\n", LONG_MIN );
          printf("Signed long maximum value: %ld\n", LONG_MAX );
          printf("Unsigned long minimum value: %lu\n", 0 );
          printf("Unsigned long maximum value: %lu\n", ULONG_MAX );
          printf("Signed long long minimum value: %lld\n", LLONG_MIN );
          printf("Signed long long maximum value: %lld\n", LLONG_MAX );
          printf("Unsigned long long minimum value: %lu\n", 0 );
          printf("Unsigned long long maximum value: %llu\n", ULLONG_MAX );
  }
```

- The short int is a signed small integer. C allows abbreviated or longer names for the same type: short, signed short, signed short int. For the unsigned version use one of these: unsigned short, unsigned short int.
- A signed integer may be declared as: int, signed, signed int. An unsigned integer may be declared as: unsigned, unsigned int.
- A signed long int may be declared using one of these names: long, signed long, ,long int, signed long int. An unsigned version may be declared as: unsigned long, unsigned long int.
- A signed long long can be declared like this: long long, singed long long, long long int, signed long long int. An unsigned can be declared as: unsigned long long, unsigned long long int.




