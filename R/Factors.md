| Function      | Package                 | Purpose & Behavior                                                                                                        |
| ------------- | ----------------------- | ------------------------------------------------------------------------------------------------------------------------- |
| `as.factor()` | **Base R**              | Converts a vector to a factor. The factor levels are **sorted alphabetically by default**.                                |
| `as_factor()` | **forcats (tidyverse)** | Also converts to a factor, but **preserves the order of the values as they appear** in the data, instead of sorting them. |

```R
x <- c("b", "c", "a")
as.factor(x)
# Levels: a b c  (alphabetical)

forcats::as_factor(x)
# Levels: b c a  (order of appearance)

```

# Manually specify factors

``factor(x, levels = NULL, labels = NULL, ordered = FALSE)``
**Manually Specifying Levels**
```R
x <- c("medium", "low", "high", "medium")

# Manually specify levels
f <- factor(x, levels = c("low", "medium", "high"))
f
```
```scss
[1] medium low    high   medium
Levels: low medium high
```

**Adding Custom Labels**
```R
f2 <- factor(x, 
             levels = c("low", "medium", "high"), 
             labels = c("L", "M", "H"))
f2
```
```scss
[1] M L H M
Levels: L M H
```

**Ordered Factor**
```R
f3 <- factor(x, 
             levels = c("low", "medium", "high"), 
             ordered = TRUE)
f3
```
Now `f3` is an **ordered factor**, so comparisons like `f3[1] > f3[2]` make sense.

The `{forcats}`package is designed for easier and more intuitive factor manipulation.

| Function               | Purpose                                                              |
| ---------------------- | -------------------------------------------------------------------- |
| `fct_relevel(f, ...)`  | Reorder levels manually (move some to front).                        |
| `fct_reorder(f, x)`    | Reorder factor levels **by a numeric variable** (e.g., mean values). |
| `fct_rev(f)`           | Reverse the order of levels.                                         |
| `fct_infreq(f)`        | Reorder levels by frequency (most common first).                     |
| `fct_lump(f, n)`       | Lump less frequent levels into “Other”.                              |
| `fct_drop(f)`          | Drop unused levels (similar to `droplevels()`).                      |
| `fct_expand(f, ...)`   | Add new levels without changing data.                                |
| `fct_collapse(f, ...)` | Combine multiple levels into one.                                    |
| `fct_cross(...)`       | Cross two or more factors (like `interaction()`).                    |