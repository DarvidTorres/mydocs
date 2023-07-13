In every computer language variables provide a means of accessing the data stored in memory. R does not provide direct access to the computer’s memory but rather provides a number of specialized data structures we will refer to as objects.

R’s base data structures can be organized by their dimensionality (1d, 2d, or nd) and whether they’re homogeneous (all contents must be of the same type) or heterogeneous (the contents can be of different types).

|---| Homogeneous | Heterogeneous |
| ----------- | ------------- | ---------- |
| 1d          | Atomic vector | List       |
| 2d          | Matrix        | Data frame |
| nd          | Array         | ---        |

# Vectors

Vectors are not arrays.

Atomic vector types:
1. logical
2. integer
3. real
4. complex
5. character (in C aka ‘string’)
6. raw

- Single numbers, such as `4.2`, and strings, such as `"four point two"` are still vectors, of length 1.
- Vectors with length zero are possible.
- A single element of a character vector is often referred to as a _character string_ or short _string_.

# Lists

- Lists have elements, each of which can contain any type of R object.
- List elements are accessed through three different [[indexing]] operations.

# NULL

- NULL is used whenever there is a need to indicate or specify that an object is absent.
- It should not be confused with a vector or list of zero length.
- It has no type and no modifiable properties.
- There is only one `NULL` object in R, to which all instances refer.
- To test for `NULL` use `is.null`.
- You cannot set attributes on `NULL`.

# Attributes

All objects except `NULL` can have one or more attributes attached to them.

- Names
	- labels the individual elements of a vector or list.
	- When an object is printed the `names` attribute, when present, is used to label the elements.
	- The `names` attribute can also be used for [[indexing]] purposes.
- Dimensions
	- The `dim` attribute is used to implement arrays.
	- The length of one or more dimensions may be zero.
	- A vector is not the same as a one-dimensional array since the latter has a `dim` attribute of length one, whereas the former has no `dim` attribute.
- Dimnames
	- Arrays may name each dimension separately using the `dimnames` attribute which is a list of character vectors.
	- The `dimnames` list may itself have names which are then used for extent headings when printing arrays.
- Classes
- Time series attributes
	- The `tsp` attribute is used to hold parameters of time series, start, end, and frequency.
	- This construction is mainly used to handle series with periodic substructure such as monthly or quarterly data.
- Copying of attributes

# Factors

- Factors are special compound objects as well as data frames.
- Factors are used to describe items that can have a finite number of values (gender, social class, etc.).
- A factor has a `levels` attribute and class `"factor"`.
- A factor may be purely nominal or may have ordered categories. In the latter case, it should be defined as such and have a `class` vector `c("ordered"," factor")`.

Factors in R Programming Language are data structures that are implemented to categorize the data or represent categorical data and store it on multiple levels. 

By default  `read.csv` imports [[files]] with `stringsAsFactors = FALSE`, for factors use: 

```R
<var> <- read.csv("<PATH>", stringsAsFactors = T) # String as factors to see how many unique values per column
<var> <- as.data.frame(unclass(stats), stringsAsFactors = TRUE) # To set strings as factors after import
```

# Data frames

A data frame is a list of vectors, factors, and/or matrices all having the same length (number of rows in the case of matrices). In addition, a data frame generally has a `names` attribute labeling the variables and a `row.names` attribute for labeling the cases.

# Variables

* List all variables in environment `ls()`
* Remove all variables in environment  `rm(list = ls())`

## Classes/types

* **Integers**: Are "forced" into R by adding "L" at the end, for instance, `x <- 2` will be stored as "double", `typeof(x <- 2)`, but if we type `x <- 2L`, the variable will be stored as an integer.
* **Complex**: are stored as `z <- 3 + 2i`
* **String**: stored with double quotes, as usual.
* **Logical**: are stored as usual