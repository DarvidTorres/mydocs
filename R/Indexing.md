In the case of an `x` basic vector type one can access the i-th element using `x[i]`.

R has three basic indexing operators, with syntax displayed by the following examples

```R
x[i]
x[i, j]
x[[i]]
x[[i, j]]
x$a
x$"a"
```

For data frames

```R
class(cars["speed"])
class(cars$"speed")
class(cars[["speed"]])
```

Using a logical vector

```R
x <- 10:20
b <- x > 15
x
b
x[b]
```

Using `which`

```R
x <- 10:20
i <- which(x > 15)
x
i
x[i]
```

A very useful operator that allows you to ask whether a set of values is present in a vector is `%in%`.

```R
x <- 10:20
j <- c(7,9,11,13)
j %in% x
which(j %in% x) # returns index in j
j[which(j %in% x)] # returns which values in j are found in x

```

Another handy similar function is `match`:

`match(j, x)` tells us that the third value in `j` is equal to the second value in `x` and that the fourth value in `j` is equal to the fourth value in `x`.

`match` is asymmetric: `match(j,x)` is not the same as `match(x,j)`.

`match(x, j)` shows that the second value in `x` is equal to the third value in `j`, etc.
