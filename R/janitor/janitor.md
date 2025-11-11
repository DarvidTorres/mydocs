```R
dt <- read_excel(
  r"(<path>)"
) |>
  clean_names() |>
  remove_empty() |>
  remove_constant() |>
  setDT()
```