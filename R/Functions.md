Every function has:
- Name
- Body of code
- Arguments

Syntax:

```R
<name> <- function(<arg1>, <arg2>, ...) {<body of code>}
```

Example:

```R
# define function
roll <- function() {
    die <- 1:6
    dice <- sample(die, size = 2, replace = TRUE)
    sum(dice)
}

# invoke the function
roll()
```

We can supply an argument for the function and then call the function with the argument, explicit or not:

```R
roll2 <- function(die2) {
    sample(die2, size = 1)
}

roll(die2 = 1:12) # explicit argument
roll(1:12) # implicit argument
```

We can supply a default value for the function and thus it will run as default unless otherwise specified:

```R

roll2 <- function(die2 = 1:12) {
    sample(die2, size = 1)
}

roll2() # takes default argument value
roll2(1:6) # takes argument provided
```

Check which arguments are defined in function:

```R
args(<function>) # See arguments for function
```

Example:

```R
args(round)
```

