Broadcasting allows these types of binary operations to be performed on arrays of different sizes.

Example:
```Python
np.arrange(3) + 5
np.ones((3, 3)) + np.arrange(3)
```

more complicated cases can involve broadcasting of both arrays.

```Python
a = np.arange(3)
b = np.arange(3)[:, np.newaxis]

print(a)
print(b)
a + b
```

Example:
```Python
np.arange(3).reshape((3, 1)) + np.arange(3)
```

![](https://i.imgur.com/RBfRTfn.png)


