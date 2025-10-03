Pattern: Missing leading zero for fractional numeric constant

Issue: -

## Description

While .1 and 0.1 mean the same thing, the latter is easier to read due to the small size of the '.' glyph.

## Examples

```r
# will produce lints
lint(
  text = "x <- .1",
  linters = numeric_leading_zero_linter()
)

lint(
  text = "x <- -.1",
  linters = numeric_leading_zero_linter()
)

# okay
lint(
  text = "x <- 0.1",
  linters = numeric_leading_zero_linter()
)

lint(
  text = "x <- -0.1",
  linters = numeric_leading_zero_linter()
)
```

## Further Reading

* [lintr - numeric_leading_zero_linter](https://lintr.r-lib.org/reference/numeric_leading_zero_linter.html)