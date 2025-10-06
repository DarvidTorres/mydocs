### 📌 The `too_many` argument

When you specify `names = c("year", "month", "day")`, you’re saying:

> “I expect this column to split into **3 parts**.”

But if a row has **more than 3 parts**, `too_many` decides what happens.

---

#### 🔹 1. `too_many = "error"` (Default)

If a row has more parts than expected, you get an **error**.

```r
library(tidyr)
df <- tibble(date = c("2025-08-27", "2024-12-05-Extra"))

df |> separate_wider_delim(
  date, delim = "-", 
  names = c("year", "month", "day"),
  too_many = "error"
)
```

❌ This fails because `"2024-12-05-Extra"` splits into **4 parts**.

---

#### 🔹 2. `too_many = "debug"`

Instead of failing, you get **extra debug columns** so you can inspect what’s going on.

```r
df |> separate_wider_delim(
  date, delim = "-", 
  names = c("year", "month", "day"),
  too_many = "debug"
)
```

✅ Adds extra columns like `.extra1`, `.extra2` for those unexpected pieces.

---

#### 🔹 3. `too_many = "drop"`

This **silently drops** any additional parts beyond what you asked for.

```r
df |> separate_wider_delim(
  date, delim = "-", 
  names = c("year", "month", "day"),
  too_many = "drop"
)
```

| year | month | day |
| ---- | ----- | --- |
| 2025 | 08    | 27  |
| 2024 | 12    | 05  |

✅ `"Extra"` is simply ignored.

---

#### 🔹 4. `too_many = "merge"` (Only for `separate_wider_delim()`)

Extra parts are **merged into the last column** (separated by the delimiter).

```r
df |> separate_wider_delim(
  date, delim = "-", 
  names = c("year", "month", "day"),
  too_many = "merge"
)
```

| year | month | day      |
| ---- | ----- | -------- |
| 2025 | 08    | 27       |
| 2024 | 12    | 05-Extra |

---

### 🧠 Quick mental model:

| Argument  | What It Does                                                        |
| --------- | ------------------------------------------------------------------- |
| `"error"` | Stops with an error if there are too many parts.                    |
| `"debug"` | Shows all extra parts in separate `.extra*` columns for inspection. |
| `"drop"`  | Discards extra parts silently.                                      |
| `"merge"` | Joins all extra parts into the last column.                         |

---

Dates rarely have unexpected parts, but `"error"` is safest because it will alert you if something is wrong with the data format.