# Objects

- In Python, an object is an entity that resides in memory.
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

- Instantiation is nothing but creating a new object/instance of a class.

Example:
```Python
class MyClass:
	"""An empty class"""
	pass

print(my_obj := MyClass())
```

# Classes

`class` creates a new [[data types|type]] of object, allowing new _instances_ of that type to be made. Each class instance can have attributes attached to it for maintaining its state. Class instances can also have methods (defined by its class) for modifying its state.

- A class is a collection of objects. 
- Unlike primitive data structures, classes are data structures that the user defines.

syntax:
```Python
class <ClassIdentifier>:
	["""<docstring>"""]
	<suite>
```

- Classes are created at runtime, and can be modified further after creation.
- Class names should normally use the `CapWords` convention.
- The first statement of the class body can optionally* be a [[Python/data types/strings/strings|string]] [[literals|literal]] that acts as the class’s documentation string, or [[docstrings|docstring]].
	- \*[[docstrings#class docstrings|docstrings]] aren't syntactically required, but you *must* add them to every class definition.

Example:
```Python
class MyClass:
	"""An empty class"""
	pass
```

When we define a class, only the description or a blueprint of the object is created. There is no memory allocation until we create its object. The objector instance contains real data or information.


