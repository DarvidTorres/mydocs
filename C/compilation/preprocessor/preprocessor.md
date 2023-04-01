# Preprocessor

Before the actual compilation of every C program it is passed through a Preprocessor. The Preprocessor looks through the program trying to find out specific instructions called Preprocessor directives that it can understand. All Preprocessor directives begin with the # (hash) symbol. C++ compilers use the same C preprocessor.

A C Preprocessor is just a text substitution tool and it instructs the [[compilation|compiler]] to do required pre-processing before the actual compilation. 

The C preprocessor, abbreviated `cpp`, is a [[macros|macro]] processor that is used automatically by the C compiler to transform programs before compilation.

All preprocessor commands begin with a hash symbol (#).

The C preprocessor provides four separate facilities:
- Inclusion of [[header files]].
- [[macros|Macro]] expansion.
- [[conditional compilation|Conditional compilation]].

Line control. If you use a program to combine or rearrange source files into an intermediate file which is then compiled, you can use line control to inform the compiler of where each source line originally came from.
