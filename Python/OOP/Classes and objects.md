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

In class-based, object-oriented programming, a **constructor** (abbreviation: `ctor`) is a special type of function called to create an object. However, unlike constructors in some other languages, `__init__()` does not actually create the object; it's rather used to initialize an object that has already been created.

- The `__init__()` method is the Python constructor.
- When you create a new object by invoking the class identifier (like `my_obj = MyClass()`), Python automatically calls the `__init__()` method of that class.
- It's not mandatory for a class to have an `__init__()` method. If you omit it, Python uses a default `__init__()` method that does nothing, which is suitable for simple classes.
- Attributes are typically defined as formal arguments in the `__init__()` method.

The first parameter of the `__init__()` method is always `self` (as a convention not as [[keyword arguments|keyword]]). It helps to differentiate between instance methods (which operate on an instance of the class) and other functions or methods.

Through `self` you can access and modify the attributes of the class instance.

Example:
```Python
class MyClass:
    """A class to demonstrate the concept of instance attributes in Python.
    
    Attributes
    ----------
    attr: any type
		Stores the value passed to the class when an instance is created.
    """
    def __init__(self, value):
        self.attr = value

my_obj = MyClass('Value')

print(my_obj.attr)
```

We can also define method attributes:
```Python
class MyClass:
    """
    A class that stores a single value and provides a method to display it.

    Attributes
    ----------
    attr : any type
        The value to be stored in the instance.

    Methods
    -------
    show_value()
        Prints the stored value to the console.
    """

    def __init__(self, value):
        self.attr = value

    def show_value(self):
        print(self.attr)

# Creating an instance of MyClass and calling show_value
my_obj = MyClass('Value')

my_obj.show_value()  # Calling the method attribute 'show_value'
```

- Method attributes in Python classes are functions that are intended to operate on instances of the class. They are defined within the class and are accessible via instances of that class.

There are two types of attributes in classes:
- **Instance methods**: These method attributes are functions that are defined within a class and are intended to be called on class instances (objects). They take self as their first parameter, which is a reference to the instance on which the method is being called. This allows the method to access other attributes and methods of the instance (and modify them if necessary).
- **Class attributes**: belong to the class itself. They are shared by all instances of the class. This means that if you modify a class attribute, it changes for all instances of that class. Class attributes are declared within a class but outside any methods, typically right below the class header. Class attributes are useful for storing constants or default values that are the same for every instance of the class.

Example:



