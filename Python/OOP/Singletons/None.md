
`None` is an example of a singleton object in Python. The [[Classes|class]] of `None` is `NoneType`:

```python
type(None)
```

If we try to call the `NoneType` [[Classes and objects#Classes|class]], we'll get back an instance of that [[Classes and objects#Classes|class]].

```python
new_none = type(None)()
```

But every instance of the `NoneType` [[Classes and objects#Classes|class]] is identical to every other instance of the `NoneType` [[Classes and objects#Classes|class]]:

```python
new_none is None
```

So there's only one instance of `NoneType` in Python, and it's `None`.

https://www.pythonmorsels.com/making-singletons/
