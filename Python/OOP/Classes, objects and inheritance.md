# Objects

- In Python, an object is a data structure.
	- A data structure is a way of organizing, managing, and storing data in a computer so that it can be accessed and modified efficiently. It's more about the relationship between the data elements and how they are organized.
- Each object in Python is identified by a unique memory address.
- This address can be thought of as the location where the object is stored in memory.
- This identity can be obtained using the `id()` function.

```Python
id('a')
```

- The reserved memory address is not the object itself, but rather a way to access or reference the object in memory.

- Each object has a [[data types|type]] which is immutable.
	- the [[data types|type]] determines what operations the object supports and also defines the possible values it can hold.
- Each object has a value.

An object contains:
1. **Attributes** (or State): Variables that are part of the object. ^d39e86
	- Usually *attribute* refers to any name following a dot `<obj_identifier>.<obj_atribute>`
	- Informally reflects the *properties* of an object.
3. **Methods**: [[Python/Functions/Functions|Functions]] that are defined inside a class and are used to define the behaviors of an object.

# Classes

In Python, a class is a user-defined prototype or template from which objects are created, encompassing a set of attributes and methods that are common to all objects of that class.
- A class is a collection of objects. 
- Unlike primitive data structures, classes are data structures that the user defines.
- `class` creates a new [[data types|type]] of object, allowing new _instances_ of that type to be made. 

syntax:
```Python
class <ClassIdentifier>:
	["""<docstring>"""]
	<suite>
```

- Classes are created at runtime, and can be modified further after creation.
- Class names should use the `CapWords` convention.
- The first statement of the class body can optionally* be a [[Python/data types/strings/strings|string]] [[literals|literal]] that acts as the class’s documentation string, or [[docstrings|docstring]].
	- \*[[docstrings#class docstrings|docstrings]] aren't syntactically required, but you *must* add them to every class definition.

Example:
```Python
class MyClass:
	"""An empty class"""
	pass
```

- Class objects support two kinds of operations: attribute references and instantiation.
- Classes can inherit attributes and methods from other classes.
- Attribute references use the standard syntax used for all attribute references in Python: `<obj_identifier>.<obj_atribute>`.
- Valid attribute names are all the names that were in the class’s namespace when the class object was created. 

Class instantiation uses function notation. Just pretend that the class object is a parameterless function that returns a new instance of the class.

- Objects are created by calling the class as if it were a function, e.g., `obj = MyClass()`.
- Instantiation is creating a new object/instance of a class.

Example:
```Python
class MyClass:
	"""An empty class"""
	pass

print(my_obj := MyClass())
```
creates a new _instance_ of the class and assigns this object to the local variable `my_obj`.

- Inheritance: A mechanism in which a new class is derived from an existing class. The derived class (child class) inherits attributes and methods from the base class (parent class).