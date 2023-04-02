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

In C programming language, generally, the special symbols have some special meaning and they cannot be used for other purposes.

Examples:

```C
[] () {} , ; * = #
```

| Brackets            | `[]` | Opening and closing of brackets are used for array element reference, which indicate single and multidimensional subscripts.                                      |
| ------------------- | ---- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Parentheses         | `()` | These special symbols are used for function calls and function parameters.                                                                                        |
| Braces              | `{}` | Opening and closing of curly braces indicates the start and end of a block of code which contains more than one executable statement.                             |
| Comma               | `, ` | It is used to separate more than one statements like separating parameters in function calls.                                                                     |
| Colon               | `: ` | It is an operator which essentially invokes something called as an initialization list.                                                                           |
| Semicolon           | `; ` | It is called as a statement terminator that indicates the end of one logical entity. That is the reason each individual statement must be ended with a semicolon. |
| Asterisk            | `* ` | It is used to create a pointer variable.                                                                                                                          |
| Assignment operator | `= ` | It is used for assigning values.                                                                                                                                  |
| Pre-processor       | `# ` | The pre-processor called as a macro processor is used by the compiler to transform your program before the actual compilation starts.                             |

# Strings

In C, a [[strings|string]] is a sequence of characters concluded with a NULL character `\0`.