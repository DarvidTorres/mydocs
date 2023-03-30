# characters

In C programming language, a `char` variable does not contain a character value itself rather the [ASCII value](https://www.cs.cmu.edu/~pattis/15-1XX/common/handouts/ascii.html) of the character variable. The ASCII value represents the character variable in numbers, and each character variable is assigned with some number range from 0 to 127. For example, the ascii value of 'A' is 65.

C defines a minimum set of characters that need to be supported on a system where C programs are written and run. Each character is given a numeric value such as A = 65, B = 66, etc. A char is an integer number big enough to at least hold the maximum value in this set, though in typical implementations it is bigger.

C does not specify whether a plain ‘char’ refers to a signed or unsigned number – that is implementation defined. If you need to be sure your char variable is signed or unsigned, specify it in the declaration like this: `unsigned char c`.

- The range of an `unsigned char` is 0 to 256, while the range of a `signed char` is -127 to 127.

