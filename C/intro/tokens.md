- Tokens are the individual elements of a program.
- We cannot create a sentence without using words; similarly, we cannot create a program in C without using tokens in C.

In the C language, the following types of tokens are available:
- Keywords
- Identifiers
- Constants
- Operators
- Special Characters
- Strings

# Keywords

- Keywords are tokens pre-defined in the C compiler.
- Each Keyword is meant to perform a specific function in a C program.
- Keywords are case sensitive and are written in lower case.

Examples:

`auto`, `double`, `int`, `struct`, `break`, `else`, `long`, `switch`, `case`, `enum`, `register`, `typedef`, `char`, `extern`, `return`, `union`, `const`, `float`, `short`, `unsigned`, `continue`, `for`, `signed`, `void`, `default`, `goto`, `sizeof`, `volatile`, `do`, `if`, `static`, `while`, `const`, `signed`, `void` and `volatile`

# Identifiers

- Identifiers are labels/names that uniquely identify variables or functions.
- Identifiers are user-defined words.

Rules for declaring identifiers:
- The identifier should consist of alphabets from a to z and A to Z.
- It may contain numerical values from 0 to 9.
- It may contain the underscore value.
- The starting character of an identifier must always be a letter.
- Commas or blank spaces cannot be specified within an identifier.
- Keywords cannot be represented as an identifier.
- There is no rule on how long an identifier can be.
- By convention, the length of the identifiers should not be more than 31 characters.

Examples of valid identifiers:

```C
foo
_foo
foo123
foo_123
foo1_
Foo
```

Examples of invalid identifiers:

```C
100foo     //started with a numerical digit
_foo,bar   //can't use comma operator
int        //keyword
Foo(100)   //circular brackets can't be used
```

# Constants

- A constant is a fixed value that cannot be altered during the execution of a program.
- Constant values cannot be changed.

We can declare a constant using:
- the [[type qualifiers#const|const]] keyword
- the [[macros#define|define directive]].

# Operators

- [[operators|Operators]] in C are special symbols used to perform specific functions
- Variables on which the operators are applied are known as operands.

# Special characters



