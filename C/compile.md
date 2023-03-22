# compiler process

1. Source code: `.c` file
2. Preprocessor: Remove comments and add code from headers
3. Compiler: Generate assembly code
4. Assembler: Generate object code (binary) 
5. Linker: Link code from file(s) and libraries to generate an executable.

# compiling

`gcc file.c`: compile file.c, it creates an a.out file in the same location.

`gcc hello.c -o given_name`: compile hello.c and create an executable given_name.

`gcc -E $CFILE > c`: runs a C file through the preprocessor and save the result into another file

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