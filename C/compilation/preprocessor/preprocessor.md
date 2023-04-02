# Preprocessor

- Before the [[compilation]], every program is passed through a preprocessor.
- The preprocessor is not part of the [[compiler]], but is a separate step in the compilation process.
- The preprocessor performs preliminary operations to source code before the compilation.
- The transformations executed by the preprocessor are lexical; the output of the preprocessor is still text.

In almost every program we see a few lines at the top of the program preceded by a hash `(#`) sign. These lines are preprocessed by the compiler before actual compilation begins.

The C preprocessor provides four separate facilities:
- Inclusion of [[header files]].
- [[macros|Macro]] expansion.
- [[conditional compilation|Conditional compilation]].

Line control. If you use a program to combine or rearrange source files into an intermediate file which is then compiled, you can use line control to inform the compiler of where each source line originally came from.
