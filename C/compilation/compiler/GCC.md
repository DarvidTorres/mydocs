- GCC stands for [GNU](https://gcc.gnu.org/) Compiler Collection.
- GCC comprises a number of compilers for different programming languages.
- GCC is a driver program that invokes the appropriate [[compilation]] programs:
	- C Preprocessor (cpp)
	- Compiler: `cc1`
		- Program `cc1` includes both the cpp and C compiler.
	- Assembler: `as`
	- Linker: `collect2`

# gcc

- The usual way to run GCC is to run the executable called `gcc`.
- The `gcc` program accepts [options](https://gcc.gnu.org/onlinedocs/gcc/Option-Summary.html) and file names as operands. 
- The most important option required while compiling a source code file is the name of the source program.

Syntax:

```C
gcc <file.c> [-c|-S|-E] [-std=standard] ...
```

When you invoke GCC, by default it performs preprocessing, compilation, assembly and linking.

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

## output file

- Change the default output file name using `-o`.

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

So, a `.i` file is preprocessed source code, so it has already been preprocessed. Therefore, it already contains:
- all [[header files]] included
- [[macros]] replaced
- [[comments]] removed

![](https://i.imgur.com/cibftll.png)

# compilation proper

Since many people refer to the entire build process as [[compilation]], this stage is often referred to as compilation proper.

Compilation refers to the processing of source code files (.c, .cc, or .cpp) and the creation of an 'object' file. This step doesn't create anything the user can actually run. Instead, the compiler merely produces the machine language instructions that correspond to the source code file that was compiled.

To stop after the stage of compilation (generate [assembly code](https://en.wikipedia.org/wiki/Assembly_language) ) proper but do not assemble (don't generate [machine code](https://en.wikipedia.org/wiki/Machine_code)) use `-S` option. The output is in the form of an assembler code file for each non-assembler input file specified.

![](https://i.imgur.com/OCWXwPv.png)

By default, the assembler file name for a source file is made by replacing the suffix `.c`, `.i`, etc., with `.s`.

# assembly

- To produce an object file use `-c` option.
- Use `-c` to assemble the source files (produce machine code), but do not link.
- The output is in the form of an object file for each source file.
- By default, the object file name for a source file is made by replacing the suffix `.c`, `.i`, `.s`, etc., with `.o`.

![](https://i.imgur.com/5gZjhfU.png)

With a project containing many `.c` files, one will typically compile first all `.c` files to `.o` files and then link everything together with the libraries.

To produce an executable, we have to call the linker.

# linking

It is possible to invoke the [[linker]] directly, but this is seldom advisable, and is typically very platform-specific. That is, options that work on Linux won't necessarily work on Solaris, AIX, macOS, Windows, and similarly for any other platform.

The linker is implicitly invoked by `gcc`:

![](https://i.imgur.com/MpQfLHc.png)

we can also produce object files for each file that we want to link, and then take the object files and actually link them:

![](https://i.imgur.com/FkwPYpp.png)

# other options

- Use the `-save-temps` option to save all intermediate code generated by the compilation process:

![](https://i.imgur.com/Qtz1bm3.png)

- Use `-m32` and `-m64` to generate code for a 32-bit or 64-bit environment:

```C
gcc -m32 main.cpp
gcc -m64 main.cpp
gcc main.cpp
```

- The 32-bit environment sets int, long and pointer to 32 bits and generates code that runs on any i386 system.
- The 64-bit environment sets int to 32 bits and long and pointer to 64 bits and generates code for AMD 's x86-64 architecture. 

# warning flags

- `-Wall`: enables all compiler's warning messages. This option should always be used, in order to generate better code.
-  `-Werror`: Make all warnings into errors.
	- `-Werror=` Make specific warnings into errors
- `Wextra`: enables some extra warning flags that are not enabled by `-Wall`
- `-pedantic`: Issue all the warnings demanded by strict ISO C and ISO C++
- `-std=`: Determine the language standard. e.g. `std=gnu89`.