Pattern: Missing use of `expect_null()`

Issue: -

## Description

`testthat::expect_null()` exists specifically for testing for `NULL` objects. `testthat::expect_equal()`, `testthat::expect_identical()`, and `testthat::expect_true()` can also be used for such tests, but it is better to use the tailored function instead.

## Examples

```r
# will produce lints
lint(
  text = "expect_equal(x, NULL)",
  linters = expect_null_linter()
)

lint(
  text = "expect_identical(x, NULL)",
  linters = expect_null_linter()
)

lint(
  text = "expect_true(is.null(x))",
  linters = expect_null_linter()
)


# okay
lint(
  text = "expect_null(x)",
  linters = expect_null_linter()
)
```

## Further Reading

* [lintr - expect_null_linter](https://lintr.r-lib.org/reference/expect_null_linter.html)