Alt + F11 to open the VBE

![VBE](https://i.imgur.com/rOGNdyN.png)

- In the VBE workbooks are called projects.
- Every project contains exactly one workbook
- A project contains:
	- [[Object model|Objects]]
	- Modules: Scripts
	- Forms: modules that have a form user-interface
	- Class Modules: Modules where you can create own objects

- Code Pane is the text editor
- immediate window is a terminal

# module

A module can hold three types of code:
- Declarations: Prototypes and variables
- Sub procedures: Return: Action
- Functions: Return: value

The best practice is to store related procedures in their own modules. For example, you might keep all the procedures that deal with importing and exporting data in a module called ImportExport, all the procedures that deal with formatting cells in a module called Formatting, and all the procedures that deal with printing in a module called Printing.

