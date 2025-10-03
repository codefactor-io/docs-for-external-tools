Pattern: Missing use of `expect_length(x, n)`

Issue: -

## Description

`testthat::expect_length()` exists specifically for testing the `length()` of an object. `testthat::expect_equal()` can also be used for such tests, but it is better to use the tailored function instead.

## Examples

```r
# will produce lints
lint(
  text = "expect_equal(length(x), 2L)",
  linters = expect_length_linter()
)

# okay
lint(
  text = "expect_length(x, 2L)",
  linters = expect_length_linter()
)
```

## Further Reading

* [lintr - expect_length_linter](https://lintr.r-lib.org/reference/expect_length_linter.html)