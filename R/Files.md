# Working directory

* `getwd()` # Get working directory
* `setwd("PATH")` # Set working directory to `PATH`
  * Example `(Windows): "C:\\Programming\\R\\R Programming A-Z"`
* ``setwd(choose.dir())`` manually set working directory
* `dir()` # See files within directory

# Here

* `here` library that allows you to use the `here()` function to create a string with the information you need to point R to a particular file.
```R 
library(here) # Library to point working directory
here() # Shows working directory exactly as getwd()
here("<cd>") # Path to subfolder cd
```

Build a path to something in a subdirectory and use it.

```r
here("one", "two", "awesome.txt")
#> [1] "/Users/jenny/rrr/here_here/one/two/awesome.txt"
cat(readLines(here("one", "two", "awesome.txt")))
#> OMG this is so awesome!
```
# Read files

* Path: Windows: use "\\\\" or "/".

```R
<var> <- read.csv("<PATH>") #inmport csv file
<var> <- read.csv(file.choose()) # Choose file manually
library(readxl) # libary to read .xlsx files
<var> <- read_excel("<PATH>", stringsAsFactors = T) # Reading a .xlsx file
library(haven) # library to read SAS (.sas7bdat), SPSS (.sav), or Stata (.dta) files
<var> <- read_dta("<PATH>", stringsAsFactors = T) # Reading a Stata file
<var> <- read_sav("<PATH>", stringsAsFactors = T) # Reading a SPSS file
<var> <- read_sas("<PATH>", stringsAsFactors = T) # Reading a SAS file
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
