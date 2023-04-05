# compilation

Compilation is the process of converting source code (human-readable code) into object code (machine-readable code). It is done with the help of the compiler.

- A compiler is a computer program that translates computer code written in one programming language (the source language) into another language (the target language).
- Compile-time is the time period when a program code is translated into a low-level code or machine code, either by a compiler or an interpreter. Compile-time is the period of time from the beginning to the end of the process.
- Runtime refers to the time when the converted code, which is now in low level or machine code, is executed. In other words, runtime refers to the time when the code does what it was written to do.

The compilation process in C involves four steps:

1. [[preprocessor|Preprocessor]]: Remove comments and add code from headers
2. [[GCC Linux|Compiler]]: Generate assembly code
3. Assembler: Generate object code (binary) `.o` file
4. Linker: Link code from file(s) and libraries to generate an executable.

![](https://i.imgur.com/rdoqxDn.png)