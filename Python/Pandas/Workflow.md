 ```Python
print(df.shape)
if df.shape[1] <= 15:
    print(df.head(), df.info(), df.describe(), sep = "\n")
elif df.shape[1] < 25:
    print(df.info())
```

