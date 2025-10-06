In short: curly braces `{ }` let you _bundle code into a single block_, and the last line in the block is what comes out.

They’re just a way to group **a sequence of expressions** together.

- Each expression inside gets evaluated in order (top to bottom).
- The value of the **last expression** is what gets returned.
So:

```r
{ 1+1; 2+2; 3+3 }
# returns 6
```

because the last thing evaluated is `3+3`.

If you just ran `{ TRUE }`, you’d get `TRUE`, because that’s the only expression inside.

---
### Example: a small function with multiple steps

```r
myfun <- function(x) {
  y <- x + 2        # first step
  z <- y^2          # second step
  z / 3             # final result
}
```

- Here, `{ }` lets you write multiple expressions inside the function.
- The **last line** (`z / 3`) is what the function returns.
- If we call:

```r
myfun(4)
```

It computes:
1. `y = 4 + 2 = 6`
2. `z = 6^2 = 36`
3. Returns `36 / 3 = 12`
---

### Why `{ }` is useful

- Without `{ }`, a function can only have **one expression**.
- With `{ }`, you can do multiple calculations, assignments, print statements, etc., and control what gets returned.
