### 📌 The `too_few` argument

When you use `separate_wider_delim()` to split a column into multiple new columns, **you tell it how many new columns you want** (via `names = c(...)`).  
If a value in your column **doesn't have enough parts to fill all those columns**, `too_few` determines what happens.

---

#### 🔹 1. `too_few = "error"` (Default)

If a row splits into fewer pieces than expected, R throws an **error** and stops:

```r
library(tidyr)
df <- tibble(date = c("2025-08-27", "2024-12"))

df |> separate_wider_delim(
  date, delim = "-", 
  names = c("year", "month", "day"),
  too_few = "error"
)
```

❌ Error, because `"2024-12"` only has 2 parts, not 3.

---

#### 🔹 2. `too_few = "debug"`

This **debugging mode** helps you see the problem by adding extra columns that show what’s missing:

```r
df |> separate_wider_delim(
  date, delim = "-", 
  names = c("year", "month", "day"),
  too_few = "debug"
)
```

✅ You’ll get extra columns like `.piece` or `.remainder` so you can locate bad rows.

---

#### 🔹 3. `too_few = "align_start"`

Missing values are **padded at the end**.  
Example:

```r
df |> separate_wider_delim(
  date, delim = "-", 
  names = c("year", "month", "day"),
  too_few = "align_start"
)
```

|year|month|day|
|---|---|---|
|2025|08|27|
|2024|12|**NA**|

---

#### 🔹 4. `too_few = "align_end"` (only in `separate_wider_delim()`)

Missing values are **padded at the start**:

```r
df |> separate_wider_delim(
  date, delim = "-", 
  names = c("year", "month", "day"),
  too_few = "align_end"
)
```

|year|month|day|
|---|---|---|
|2025|08|27|
|**NA**|2024|12|

---

### 🧠 Quick mental model:

- `"align_start"` → Start filling from **left**, pad `NA`s **on the right**.
    
- `"align_end"` → Start filling from **right**, pad `NA`s **on the left**.
    
- `"error"` → Stop execution when something’s missing.
    
- `"debug"` → Help diagnose the issue interactively.

`"align_start"` is best, because dates naturally start with the year, then month, then day, so if the day is missing, we just add `NA` at the **end**.