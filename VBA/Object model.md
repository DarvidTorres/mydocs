# Hierarchy

There are many objects in the hierarchy.

Application
- Addin
- Window
- Workbook
	- Chart
	- Name
	- VBProject
	- Window
	- Worksheet
		- Comment
		- Hyperlink
		- Name
		- PageSetup
		- PivotTable
		- Range
			- Excel does not have a Cell object. A cell is a Range that consists of one element.
- WorksheetFunction

Collections:
- Workbooks
- Worksheets
- Charts
- Sheets

# Referencing

To refer to a Workbook object, use dot operator following hierarchy structure.

>Start with the Application object like in the following code:
>`Application.Workbooks.Item("Book1").Path`

All collection objects have an Item property to get to a singular instance of an object they collect. A collection’s Item property takes one argument. That argument can be a string (enclosed in double quotes) or an integer.

>The following code returns the first worksheet of the second workbook:
>`Application.Workbooks.Item(2).Worksheets.Item(1)`

The left-most worksheet in Excel is the first worksheet in the collection.

Item is the default property for every collection, making the following code lines equivalent:

```VBA
Application.Workbooks.Item("Book1.xlsx").Worksheets.Item(2).Range("A1").Value
Application.Workbooks("Book1.xlsx").Worksheets(2).Range("A1").Value
```

The Application object is always assumed.

```VBA
Application.Workbooks("Book1.xlsx").Worksheets(2).Range("A1").Value
Workbooks("Book1.xlsx").Worksheets(2).Range("A1").Value
```

We can assume active workbook:

```VBA
Workbooks("Book1.xlsx").Worksheets(2).Range("A1").Value
Worksheets(2).Range("A1").Value
```

We can assume active worksheet:

```VBA
Worksheets(2).Range("A1").Value
Range("A1").Value
```

You almost never need the Application object in your reference, but you may need the Workbook
object.

# Properties & Methods

To accomplish anything meaningful, you must do one of two things:
- Read or modify an object’s properties.
	- `<object> = <value>`
- Call a method to be used with an object.
	- `<object>.<method>`







