- In Python, an object is a [[data structures|data structure]].
- Each object has a [[data types|type]] which is immutable.
	- the [[data types|type]] determines what operations the object supports and also defines the possible values it can hold.
- Each object has a value.

An object contains:
1. **Attributes** (or State): Variables that are part of the object. ^d39e86
	- Usually *attribute* refers to any name following a dot `<obj_identifier>.<obj_atribute>`
	- Informally reflects the *properties* of an object.
3. **Methods**: [[Python/Functions/Functions|Functions]] that are defined inside a class and are used to define the behaviors of an object.

- Each object in Python is identified by a unique memory address.
- This address can be thought of as the location where the object is stored in memory.
- This identity can be obtained using the `id()` function.

```Python
id('a')
```

- The reserved memory address is not the object itself, but rather a way to access or reference the object in memory.