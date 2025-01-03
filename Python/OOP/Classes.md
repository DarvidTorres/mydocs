
In Python, a class is a user-defined prototype or template from which objects are created, encompassing a set of attributes and methods that are common to all objects of that class.
- A class is a collection of objects. 
- Unlike primitive data structures, classes are data structures that the user defines.
- `class` creates a new [[data types|type]] of object, allowing new _instances_ of that type to be made.

- Class identifiers should be `CapWords`

syntax:
```Python
class <ClassIdentifier>:
	["""<docstring>"""]
	<suite>
```

- Classes are created at runtime, and can be modified further after creation.
- Class names should use the `CapWords` convention.
- The first statement of the class body can optionally* be a [[Python/data types/Strings/strings|string]] [[literals|literal]] that acts as the class’s documentation string, or [[docstrings|docstring]].
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

Generally speaking, instance variables are for data unique to each instance and class variables are for attributes and methods shared by all instances of the class:
- **Instance methods**: These method attributes are functions that are defined within a class and are intended to be called on class instances (objects). They take self as their first parameter, which is a reference to the instance on which the method is being called. This allows the method to access other attributes and methods of the instance (and modify them if necessary).
- **Class attributes**: belong to the class itself. They are shared by all instances of the class. This means that if you modify a class attribute, it changes for all instances of that class. Class attributes are declared within a class but outside any methods, typically right below the class header. Class attributes are useful for storing constants or default values that are the same for every instance of the class.

Example:

```Python
class Dog:
    """
    A class representing a dog with a species class attribute and a name instance attribute.

    Class Attributes
    ----------------
    species : str
        The species of the dog. Default is "Canis lupus familiaris".

    Attributes
    ----------
    name : str
        The name of the dog instance.

    Methods
    -------
    __init__(name: str)
        Constructs all the necessary attributes for the dog object.
    """

    species = "Canis lupus familiaris"  # Class attribute

    def __init__(self, name):
        self.name = name  # Instance attribute

# Creating instances of Dog
dog1 = Dog("Rex")
dog2 = Dog("Fido")

# Accessing class attribute
print(Dog.species)  # Outputs: Canis lupus familiaris
print(dog1.species) # Outputs: Canis lupus familiaris

# Accessing instance attribute
print(dog1.name)  # Outputs: Rex
print(dog2.name)  # Outputs: Fido

# Modifying class attribute via an instance
dog1.species = "Canis lupus"
print(dog1.species) # Outputs: Canis lupus
print(dog2.species) # Still outputs: Canis lupus familiaris
print(Dog.species)  # Still outputs: Canis lupus familiaris

```

