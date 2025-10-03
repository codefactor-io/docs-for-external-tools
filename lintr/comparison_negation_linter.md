Pattern: Use of `!(x == y)`

Issue: -

## Description

`!(x == y)` is harder to comprehend compared to `x != y`. The same is true of other negations of simple comparisons like `!(x > y)` and `!(x <= y)`.

## Examples

```r
# will produce lints
lint(
  text = "!x == 2",
  linters = comparison_negation_linter()
)

lint(
  text = "!(x > 2)",
  linters = comparison_negation_linter()
)

# okay
lint(
  text = "!(x == 2 & y > 2)",
  linters = comparison_negation_linter()
)

lint(
  text = "!(x & y)",
  linters = comparison_negation_linter()
)

lint(
  text = "x != 2",
  linters = comparison_negation_linter()
)
```

## Further Reading

* [lintr - comparison_negation_linter](https://lintr.r-lib.org/reference/comparison_negation_linter.html)