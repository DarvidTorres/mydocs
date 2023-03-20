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
- WorksheetFunction

Collections:
- Workbooks
- Worksheets
- Charts
- Sheets

To get to a Workbook object, you can start with the Application object like in the following code: `Application.Workbooks.Item("Book1").Path`. All collection objects have an Item property to get to a singular instance of an object they collect. A collection’s Item property takes one argument. That argument can be a string (enclosed in double quotes) or an integer.

The following code returns the first worksheet of the second workbook:
`Application.Workbooks.Item(2).Worksheets.Item(1)`

Worksheets are ordered the same way as in Excel. The left-most worksheet is the first worksheet in the collection.



