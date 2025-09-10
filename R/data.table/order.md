```R
library(nycflights13)
flights_dt <- as.data.table(copy(flights)) # Copy from package data frame
flights_dt[order(origin, -dest)]
```
### 1. What `order()` returns

The function `order()` doesn’t sort the data itself. Instead, it returns a vector of row indices that will arrange the data in the requested order.

For example:

```r
order(c(5, 2, 9))
# [1] 2 1 3
```

That means:

- put the 2nd element first (`2`),
- then the 1st element (`5`),
- then the 3rd element (`9`).

So when you do:

```r
flights_dt[order(origin, -dest)]
```

you’re saying:

> “Take the rows of `flights_dt`, reordered according to the order of `origin` (ascending), breaking ties by `dest` (but in descending order).”

---

### 2. Why the minus sign works

Normally, `-` only makes sense for numbers. But inside `order()` within a `data.table`, the minus sign has been extended to also mean “sort descending” even for character columns.

So `-dest` tells `data.table`: “reverse the usual sorting order of `dest`.”

---

### 3. The difference between `order()` and `setorder()`

- `flights_dt[order(...)]` creates a **new reordered copy** of your data (though optimized under the hood with `forder()`).
- `setorder(flights_dt, origin, -dest)` reorders the rows **by reference** (no copy made). After this, `flights_dt` itself is permanently sorted.

---

👉 Quick check for you:  
What do you think this would do?

```r
setorder(flights_dt, -month, dep_delay)
```

Take a guess: what’s the sorting order here?
- First key: `-month` → months sorted from **December down to January**.
- Second key: `dep_delay` → within each month, rows are ordered by **increasing departure delay**.
- And because we used `setorder()`, the sort is **by reference** — so `flights_dt` itself is changed, no new object is created.
---

✨ Quick memory hook:  
Think of `setorder()` like saying _“set the table in this order”_ — it rearranges the actual table you have.  
Whereas `x[order(...)]` is more like _“give me a freshly plated copy”_.
