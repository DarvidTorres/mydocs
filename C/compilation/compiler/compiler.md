- A compiler is a computer program that translates computer code written in one programming language (the source language) into another language (the target language).
- Compile-time is the time period when a program code is translated into a low-level code or machine code, either by a compiler or an interpreter. Compile-time is the period of time from the beginning to the end of the process.
- Runtime refers to the time when the converted code, which is now in low level or machine code, is executed. In other words, runtime refers to the time when the code does what it was written to do.
- GCC stands for [GNU](https://gcc.gnu.org/) Compiler Collection.
- GCC is a [[compilation|compiler]] system.

# gcc

- The usual way to run GCC is to run the executable called `gcc`.
- The `gcc` program accepts [options](https://gcc.gnu.org/onlinedocs/gcc/Option-Summary.html) and file names as operands. 
- The most important option required while compiling a source code file is the name of the source program.

Syntax:

```C
gcc <file.c> [-c|-S|-E] [-std=standard] ...
```

When you invoke GCC, it normally does preprocessing, compilation, assembly and linking.

Example:

Given a file named `source.c`, we can create an executable by running:

```C
gcc source.c
```

This will compile `file.c` and give an output file in the same directory as `file.c`, the output file default name is `a.out`, which can be executed using `./a.out`.

![](https://i.imgur.com/gFEHipy.png)

Note:
- `$?` is a Bash [[special variables|built-in variable]] that stores the exit status of a command, function, or the script itself. 
- `$?` reads the exit status of the last command executed.
- After a function returns, `$?` gives the exit status of the last command executed in the function.

The different options of `gcc` command allow the user to stop the compilation process at different stages.

# output file

- Change the default output file name.

Syntax:

```C
-o <file>
```

- Place output in `<file>`. This applies regardless to whatever sort of [output](https://gcc.gnu.org/onlinedocs/gcc/Overall-Options.html#Overall-Options) is being produced, whether it be an executable file, an object file, an assembler file or preprocessed C code.
	- If `-o` is not specified, the default is to put an executable file in `a.out`.

![](https://i.imgur.com/XSIioWd.png)

# preprocessing

To stop the compiler at the preprocessing stage (before compilation) use `-E` option.

![](https://i.imgur.com/vEekSpI.png)

Using the `-E` option, we get C code as [[input and output|standard output]], but there's no new file, as the [[preprocessor]] doesn't create executables.

We can create a new file that contains the preprocessed source code using `-o` option.

![](https://i.imgur.com/XtemrPe.png)

Though not required, preprocessed files (files that have been run through the preprocessor) are indicated with the `.i` extension. It is usually this extension which is characteristic of files created as the preprocessor output.

So, an `file.i` indicates C source code that should not be preprocessed (as it has been preprocessed already).

![](https://i.imgur.com/cibftll.png)


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