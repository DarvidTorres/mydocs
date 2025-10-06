# Arithmetic mean (average)

## Average of averages

- An **average** is supposed to represent _every individual in the group_.
- If you take an **average of averages**, you’re treating each group as if it has the same number of individuals, no matter how large or small it actually is. That means a small group’s results count just as much as a huge group’s results — which distorts the picture.
- A **weighted average**, on the other hand, adjusts for the actual size of each group. Bigger groups have more influence, smaller groups have less. That way, every single individual counts equally, no matter which group they belong to.

**Weighted average (the correct overall average)**

$$\frac{n_1a_1 + n_2a_2+n_3a_3}{n_1+n_2+n_3}$$​
**Average of averages (the incorrect shortcut):**

$$\frac{a_1+a_2+a_3}{3}$$
- The **weighted average** multiplies each group’s average by the number of students, then divides by the total students.
- The **average of averages** just treats each group as equal, no matter how many individuals are in each.

| Mean Type           | Formula (for values $x_1, x_2, …, x_n$)                              | Best suited for                                     | Typical use cases                                  | Limitations                                              | Notes                                                                                                                                        |
| ------------------- | -------------------------------------------------------------------- | --------------------------------------------------- | -------------------------------------------------- | -------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| **Arithmetic mean** | $$\frac{x_1 + x_2 + \cdots + x_n}{n}$$                               | Additive, linear, symmetric data                    | Heights, test scores, sensor readings              | Distorted by skew/outliers                               |                                                                                                                                              |
| **Geometric mean**  | $$(x_1\cdot x_2 \cdot \ldots x_n)^\frac{1}{n}$$                      | Multiplicative, exponential, lognormal, skewed data | Compound interest, growth rates, normalized ratios | Only valid for $x_i>0$; units lost in interpretation     | Make sure all your rates are expressed as multiplicative factors greater than 0 (i.e., <br>$x_i = 1+𝑟_i$) rather than percentages directly. |
| **Harmonic mean**   | $$\frac{n}{\frac{1}{x_1} + \frac{1}{x_2} + \cdots + \frac{1}{x_n}}$$ | Averaging ratios (with focus on numerator), rates   | Travel speeds, P/E ratios, F1-score in ML          | Very sensitive to small values; only valid for $x_i > 0$ | 0                                                                                                                                            |

