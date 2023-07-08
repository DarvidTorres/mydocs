Factors in R Programming Language are data structures that are implemented to categorize the data or represent categorical data and store it on multiple levels. 



By default  `read.csv` imports [[files]] with `stringsAsFactors = FALSE`, for factors use: 

```R
<var> <- read.csv("<PATH>", stringsAsFactors = T) # String as factors to see how many unique values per column
<var> <- as.data.frame(unclass(stats), stringsAsFactors = TRUE) # To set strings as factors after import
```