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

To continue a single line of code (also known as a statement) from one line to the
next, end the first line with a space followed by an underscore (`_`). Then continue
the statement on the next line.

```VBA
Selection.Sort Key1:=Range("A1"), _
Order1:=xlAscending, Header:=xlGuess, _
Orientation:=xlTopToBottom
```

An example:

```VBA
Sub GuessName()
    Msg = "Is your name " & Application.UserName & "?"
    Ans = MsgBox(Msg, vbYesNo)
    If Ans = vbNo Then MsgBox "Oh, never mind."
    If Ans = vbYes Then MsgBox "I must be psychic!"
End Sub
```

Use F5 to run the macro, or F8 to run line by line.

