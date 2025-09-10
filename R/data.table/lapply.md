

---

### 2. Two lines

```r
DT[, lapply(.SD, mean)]
DT[, lapply(DT, mean)]
```

- The first is the canonical way: `.SD` gives the “current subset of data,” and `lapply` goes column by column.
- The second _can_ work, but it’s not the same: here you’re telling R “take the whole `DT` object and lapply over it,” which ignores the grouping behavior of `by`.

---

### 3. Key difference when you add `by`

```r
DT[, lapply(.SD, mean), by = group]
```

- `.SD` is now **just the rows for each group**.
- `DT` would still be the entire dataset — grouping wouldn’t affect it.
So `.SD` is essential for grouped operations.

---

✅ Summary:
- Without `by`, `lapply(.SD, mean)` _looks like_ `lapply(DT, mean)` but is more idiomatic.
- With `by`, only `.SD` “shrinks” to the group’s data.
