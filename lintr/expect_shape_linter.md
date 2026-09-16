Pattern: Missing use of `testthat::expect_shape()`

Issue: -

## Description

`testthat::expect_shape()` exists specifically for testing the `nrow()`, `ncol()`,
or `dim()` of an object. `testthat::expect_equal()` and
`testthat::expect_identical()` can also be used for such tests,
but it is better to use the tailored function instead.

## Examples

```r
# will produce lints
lint(
  text = "expect_equal(nrow(x), 4L)",
  linters = expect_shape_linter()
)

lint(
  text = "expect_equal(dim(x), c(2L, 3L))",
  linters = expect_shape_linter()
)

# okay
lint(
  text = "expect_shape(x, nrow = 4L)",
  linters = expect_shape_linter()
)

lint(
  text = "expect_shape(x, dim = c(2L, 3L))",
  linters = expect_shape_linter()
)
```

## Further Reading

* [lintr - expect_shape_linter source](https://github.com/r-lib/lintr/blob/main/R/expect_shape_linter.R)
