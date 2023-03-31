the `const` keyword prevents changes to defined variables.

```c
const int myNum = 15;  // myNum will always be 15
myNum = 10;  // error: assignment of read-only variable 'myNum'
```

Constants must be defined with value:

```c
const int minutesPerHour;
minutesPerHour = 60; // error
```

it is considered good practice to declare them with uppercase. It is not required, but useful for code readability and common for C programmers:

```c
const int BIRTHYEAR = 1980;
```