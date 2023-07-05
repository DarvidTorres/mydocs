

# Packages

* ``print(.packages())`` # List loaded packages
* ``detach("package:<package_name>")`` # Unload packages
* load packages if not loaded already

```R
if(! "<package_name>" %in% (.packages())){
  library("<package_name>")
  (.packages())
}
```

* ``require`` The required package will load if not loaded already

# Files

## Working directory

* `getwd()` # Get working directory
* `setwd("PATH")` # Set working directory to `PATH`
  * Example `(Windows): "C:\\Programming\\R\\R Programming A-Z"`
* ``setwd(choose.dir())`` manually set working directory
* `dir()` # See files within directory
* `here` library that allows you to use the `here()` function to create a string with the information you need to point R to a particular file.
```R 
library(here) # Library to point working directory
here() # Shows working directory exactly as getwd()
here("<cd>") # Path to subfolder cd
```

## Read files

* Path: Windows: use "\\\\" or "/".

```R
<var> <- read.csv("PATH", stringsAsFactors = T) # String as factors to see how many unique values per column
<var> <- read.csv(file.choose()) # Choose file manually
library(readxl) # libary to read .xlsx files
<var> <- read_excel("PATH", stringsAsFactors = T) # Reading a .xlsx file
library(haven) # library to read SAS (.sas7bdat), SPSS (.sav), or Stata (.dta) files
<var> <- read_dta("PATH", stringsAsFactors = T) # Reading a Stata file
<var> <- read_sav("PATH", stringsAsFactors = T) # Reading a SPSS file
<var> <- read_sas("PATH", stringsAsFactors = T) # Reading a SAS file
```

```R
here("<file_name>") # File path in working directory
here("<cd>", "<file_name>") # File path in subfolder cd
<var> <- read<extension>(here("<cd>", "<file_name>")) # Import using here()
```

## Export files

```R 
write.csv(<df>, here("df.csv"), row.names=FALSE)
```

## R objects

Makes it faster to import/export data
```R
save.image("PATH\\name_of_file.RDATA") # Create image file
load("PATH\\name_of_file.RDATA") # Read image file
```

## Tables manually

```R
mydata <- data.frame(age=numeric(0), gender=character(0), weight=numeric(0))
mydata <- edit(mydata)
```

# Data frame structure

```R
str(<df>) # Structure of the <df>
skimr::skim(movies) # Requires skimr package
count(<df>, <col1>, <col2>, <col3>) # Show unique values and count, factors, requieres dplyr / tidyverse
as.data.frame(unique(mpg$manufacturer)) # Show unique values, specially useful for factors
distinct(<df>, <col1>, <col2>, .keep_all = TRUE) # Unique values by pairs, requieres dplyr / tidyverse
summary(<df>) # Shows quartiles of variable
nrow(<df>) # Number of rows
ncol(<df>) # Number of col
dim(<df>) # Number of rows and columns
head(<df>, <n>) # First <n> rows
tail(<df>, <n>) # Last <n> rows
nrow(<df>) ; ncol(<df>) # Number of rows and columns in same line
```

# Preprocessing

```R
colnames(<df>)
tolower(colnames(<df>)) # lowercase colnames
print(as.data.frame(colnames(hw))) # print all colnames AND get their index
colnames(<df>)[<int.>] <- "<colx>" # change the name of column <int.>
colnames(<df>)[c(<int1>, <int2>)] <- c("<col1>", "<col2>") # change the name of cols <int1> and <int2>
```

# Subseting

## Matrix

```R
rbind() 
```

## Using brackets

It's not recommended to use bracket syntax if we subset a single row or a single column, because the object-type changes from data frame to a vector

* `<data_frame>[<rows>, <columns>] #Left empty to get all rows/columns`
* `<data_frame>[c(<row_x>, <row_y>), c(<column_x>, <column_y>)]`
* `is.data.frame(data[,1]) # All rows, but column 1 only`
* `is.data.frame(data[,1, drop=F]) # All rows, but column 1 only while maintaining data frame type`

## Using dollar sign $

Dollar sign to access columns from data frame.
* `<data frame>$<column> #Column must be imput as string`

We can operate values of columns using dollar sign
* `<data frame>$<column> */+/-/%% <data frame>$<column>`

Add columns

* `<data frame>$<new_column> <- <data frame>$<column> * <data frame>$<column>`

Remove columns
* `<data_frame>$<column> <- NULL`

# Variables

* List all variables in environment `ls()`
* Remove all variables in environment  `rm(list = ls())`

## Classes/types

* **Integers**: Are "forced" into R by adding "L" at the end, for instance, `x <- 2` will be stored as "double", `typeof(x <- 2)`, but if we type `x <- 2L`, the variable will be stored as an integer.
* **Complex**: are stored as `z <- 3 + 2i`
* **String**: stored with double quotes, as usual.
* **Logical**: are stored as usual

## Graphs

* Factor columns `<df>[<columns>] <- lapply(<df>[<cols>], factor)`
* Clear all graphs `graphics.off()`
* Graphs are objects and can be stored as variables
```R
p <- ggplot(
  base,
  aes(tomatoes_rating, audience_rating, size = budget_m, color = genre)) + 
  geom_point()
```
* To acces values of graph as variable use `str(<var>)`

## Simple built-in functions

* Concatenate using `paste(var1, var2)` will be stored as string with a space between the characters
* `seq(<start>, <end>, <step>)` create a sequence
* `rep(<object>, <times>)` generate a vector that contains the same object multiple times

## Logical operators

* `<`	less than
* `<=`	less than or equal to
* `>`	greater than
* `>=`	greater than or equal to
* `==`	Equal to
* `!`	Not
* `|`	OR
* `&`   AND
* ``isTRUE(x)``	test if x is TRUE


## Loops

* While
```
while(<condition>){
  <instruction>
}
```
* For
```
for(<var> in <vector>){
  <instruction>
}
```
* If
```
if (<condition>){
  <instruction>
} else{
  <instruction>
}

if (<condition>){
  <instruction>
} else if{
  <instruction>
} else{
  <instruction>
}
```

**Exercise**: Using `rnorm(1)`, check whether x falls in (-$\infty$, -1), [-1, 1], (1, $\infty$)

```
x <- rnorm(1)
if (x > 1){
  print("Greater than 1")
} else if(x >= -1){
  print("Between -1 and 1")
} else{
  print("Less than -1")
}
```

**Exercise**: For sample `N` of `n` numbers generated by `rnorm()`, check whether the media of `N` approaches 68.2 (as expected)

```R
N <- 100
counter <- 1
for (n in rnorm(N)){
  if ((n > -1) & (n < 1)){
    print(n)
    print(counter)
    counter <- counter + 1
  }
}
print(counter / N)
```

# tidyverse

This package includes:
* ggplot2
* tibble
* purrr
* dplyr
* tidyr
* readr
* forcats

## dplyr

### count

```R
count(<df>, <col1>, <col2>, .sort = TRUE) # order of cols matter, sort goes by count (takes ALL the data, not by groups)
```

### group_by

`group_by(<df>, <col1>, <col2>, .add = <FALSE>)`

`ungroup(x, ...)`

### summarise



### select (columns)

* `select(<df>, <col>)`
* Examples

```R
select(<df>, 3:ncol(<df>)-3) # Columns from 3 to last - 3
select(<df>, c(<colz>, <coly>, <colx>)) # Columns z, y, x in that order
```

### Remove columns

```R
<df> <- select(<df>, -<var_to_delete>)
```

### Renamecolumns

```R
rename(<df>, <new_col_name1> = <old_col_name1>, <new_col_name2> = <old_col_name2>) # Changes the names of individual variables
```

The ``rename()`` function doesn't substitute names in the `<df>` object, for that we need to assign the value to a variable

```R
<var> <- rename(<df>, <new_col_name1> = <old_col_name1>, <new_col_name2> = <old_col_name2>) # Assings the data frame to <var> with new names
```

### mutate / transmute

Mutate creates new variables and (by default) keeps the rest.
Transmute creates new variables and drops the rest.

```R
mutate(
  <df>,
  <new_var1> = <operation_to_row_values>,
  .keep = c("all", "used", "unused", "none"),
  .before = NULL,
  .after = NULL
)
```
Examples:

```R
# By default, new columns are placed on the far right.
# Experimental: you can override with `.before` or `.after`
df <- tibble(x = 1, y = 2)
df %>% mutate(z = x + y)
df %>% mutate(z = x + y, .before = 1)
df %>% mutate(z = x + y, .after = x)
# By default, mutate() keeps all columns from the input data.
# Experimental: You can override with `.keep`
df <- tibble(x = 1, y = 2, a = "a", b = "b")
df %>% mutate(z = x + y, .keep = "all") # the default
df %>% mutate(z = x + y, .keep = "used")
df %>% mutate(z = x + y, .keep = "unused")
df %>% mutate(z = x + y, .keep = "none") # same as transmute()
```

### filter

``filter(<df>, <criteria>)``

Examples

```R
filter(mpg, year == 1999)
```

### arrange

`arrange(<df>, <col1>, desc(<col2>)) # order matters`

### distinct

Remove rows with duplicate values

`distinct(<df>, <col>)`

# Strings

We can concatenate strings using the `paste()` and `paste0()` functions (the result is always a vector):

```R 
paste(<vector1>, "<string1>", <vector2>, "<string2>") # Concatenate the arguments, adding a space bewteen them
paste0(<vector1>, "<string1>", <vector2>, "<string2>") # Concatenate without adding space
paste/0(..., collapse = "<string>") # Collapse the string vector to a single string using the <string> separator, no difference to use paste or paste0
paste0(..., collapse) is equivalent to paste(..., sep = "", collapse), slightly more efficiently.
```

Examples

```R
# Using paste
nth <- paste(1:12, c("st", "nd", "rd", rep("th", 9)))
(nth)
paste(nth, collapse = ", ")

# Using paste0
nth <- paste0(1:12, c("st", "nd", "rd", rep("th", 9)))
(nth)
paste0(nth, collapse = ", ")
```

