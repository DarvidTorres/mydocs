Linking is the process of collecting and combining various pieces of code and data into a single file that can be loaded (copied) into memory and executed.

Here is where all of the object files and any libraries are linked together to make your final program. - This includes both the object files that the compiler created from your source code files as well as object files that have been pre-compiled for you and collected into library files. These files have names which end in `.a` or `.so`.

- Like the [[preprocessor]], the linker is a separate program, often called `ld` (but [[GCC|Linux]] uses `collect2`).
- Linking refers to the creation of a single executable file from multiple object files (`.o`, `.obj`).