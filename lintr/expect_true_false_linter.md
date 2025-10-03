Pattern: Missing use of `expect_true(x)`

Issue: -

## Description

`testthat::expect_true()` and `testthat::expect_false()` exist specifically for testing the `TRUE`/`FALSE` value of an object. `testthat::expect_equal()` and `testthat::expect_identical()` can also be used for such tests, but it is better to use the tailored function instead.

## Examples

```r
# will produce lints
lint(
  text = "expect_equal(x, TRUE)",
  linters = expect_true_false_linter()
)

lint(
  text = "expect_equal(x, FALSE)",
  linters = expect_true_false_linter()
)

# okay
lint(
  text = "expect_true(x)",
  linters = expect_true_false_linter()
)

lint(
  text = "expect_false(x)",
  linters = expect_true_false_linter()
)
```

## Further Reading

* [lintr - expect_true_false_linter](https://lintr.r-lib.org/reference/expect_true_false_linter.html)