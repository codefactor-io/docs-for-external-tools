Pattern: Missing use of `testthat::expect_named()`

Issue: -

## Description

`testthat::expect_named()` exists specifically for testing the `names()` of an object. `testthat::expect_equal()` can also be used for such tests, but it is better to use the tailored function instead.

## Examples

```r
# will produce lints
lint(
  text = 'expect_equal(names(x), "a")',
  linters = expect_named_linter()
)

# okay
lint(
  text = 'expect_named(x, "a")',
  linters = expect_named_linter()
)

lint(
  text = 'expect_equal(colnames(x), "a")',
  linters = expect_named_linter()
)

lint(
  text = 'expect_equal(dimnames(x), "a")',
  linters = expect_named_linter()
)
```

## Further Reading

* [lintr - expect_named_linter](https://lintr.r-lib.org/reference/expect_named_linter.html)