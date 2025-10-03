Pattern: Missing use of `expect_s3_class()`

Issue: -

## Description

`testthat::expect_s3_class()` exists specifically for testing the class of S3 objects. `testthat::expect_equal()`, `testthat::expect_identical()`, and `testthat::expect_true()` can also be used for such tests, but it is better to use the tailored function instead.

## Examples

```r
# will produce lints
lint(
  text = 'expect_equal(class(x), "data.frame")',
  linters = expect_s3_class_linter()
)

lint(
  text = 'expect_equal(class(x), "numeric")',
  linters = expect_s3_class_linter()
)

# okay
lint(
  text = 'expect_s3_class(x, "data.frame")',
  linters = expect_s3_class_linter()
)

lint(
  text = 'expect_type(x, "double")',
  linters = expect_s3_class_linter()
)
```

## Further Reading

* [lintr - expect_s3_class_linter](https://lintr.r-lib.org/reference/expect_s3_class_linter.html)