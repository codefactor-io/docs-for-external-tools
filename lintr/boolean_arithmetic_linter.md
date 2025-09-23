Pattern: Use of `length(which(x == y)) == 0`

Issue: -

## Description

`length(which(x == y)) == 0` is the same as `!any(x == y)`, but the latter is more readable and more efficient.

## Examples

```r
# will produce lints
lint(
  text = "length(which(x == y)) == 0L",
  linters = boolean_arithmetic_linter()
)

lint(
  text = "sum(grepl(pattern, x)) == 0",
  linters = boolean_arithmetic_linter()
)

# okay
lint(
  text = "!any(x == y)",
  linters = boolean_arithmetic_linter()
)

lint(
  text = "!any(grepl(pattern, x))",
  linters = boolean_arithmetic_linter()
)

```

## Further Reading

* [lintr - Available linters](https://lintr.r-lib.org/reference/index.html)