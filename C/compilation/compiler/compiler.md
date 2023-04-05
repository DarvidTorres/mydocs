- A compiler is a computer program that translates computer code written in one programming language (the source language) into another language (the target language).
- Compile-time is the time period when a program code is translated into a low-level code or machine code, either by a compiler or an interpreter. Compile-time is the period of time from the beginning to the end of the process.
- Runtime refers to the time when the converted code, which is now in low level or machine code, is executed. In other words, runtime refers to the time when the code does what it was written to do.
- GCC stands for [GNU](https://gcc.gnu.org/) Compiler Collection.
- GCC is a [[compilation|compiler]] system.

# gcc

- The usual way to run GCC is to run the executable called `gcc`.
- The `gcc` program accepts [options](https://gcc.gnu.org/onlinedocs/gcc/Option-Summary.html) and file names as operands. 
- The most important option required while compiling a source code file is the name of the source program.
- The different options of `gcc` command allow the user to stop the compilation process at different stages.

Syntax:

```C
gcc <file.c> [-c|-S|-E] [-std=standard]
```

When you invoke GCC, it normally does preprocessing, compilation, assembly and linking.

Example:

Given a file named `source.c`, we can create an executable by running:

```C
gcc source.c
```

This will compile `file.c` and give the output file as `a.out` file which is the default name of output file given by `gcc` compiler, which can be executed using `./a.out`.

![](https://i.imgur.com/F4mwCfa.png)



`gcc file.c`: compile file.c, it creates an a.out file in the same location.

`gcc hello.c -o given_name`: compile hello.c and create an executable given_name.

`gcc -E $CFILE -o c`: runs a C file through the preprocessor and save the result into another file

`gcc -E main.c > main.i`: The output of preprocessing stage can be produced using the -E option.

`gcc -S main.c > main.s`: The assembly level output can be produced using the -S option.

`tr .c .s | gcc -S $CFILE > .c`: Write a script that generates the assembly code of a C code and save it in an output file.

`gcc -c file.c`: Compile or assemble the source files, but do not create an executable (outputs a `file.o` file)

"Compile only" `gcc -c` produces only object file. To produce an executable, you have to call linker again. With a project containing many `.c` files, one will typically compile first all `.c` files to `.o` files and then link everything together with the libraries.

`gcc main.c server.c` compile `main.c` then take function declarations from `server.c` (link) and produce a single executable `a.out` (it doesn't produce two executables for each file, but one as the linker was invoked).

```C
gcc -m32 main.cpp
gcc -m64 main.cpp
gcc main.cpp
```

`-m32 -m64` Generate code for a 32-bit or 64-bit environment. 

- The 32-bit environment sets int, long and pointer to 32 bits and generates code that runs on any i386 system.
- The 64-bit environment sets int to 32 bits and long and pointer to 64 bits and generates code for AMD 's x86-64 architecture. 


# warning flags

- `-Wall`: enables all compiler's warning messages. This option should always be used, in order to generate better code.
-  `-Werror`: Make all warnings into errors.
	- `-Werror=` Make specific warnings into errors
- `Wextra`: enables some extra warning flags that are not enabled by `-Wall`
- `-pedantic`: Issue all the warnings demanded by strict ISO C and ISO C++
- `-std=`: Determine the language standard. e.g. `std=gnu89`.