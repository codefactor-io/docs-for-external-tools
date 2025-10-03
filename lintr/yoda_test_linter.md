Pattern: Yoda condition

Issue: -

## Description

Yoda tests use `(expected, actual)` instead of the more common `(actual, expected)`. This is not always possible to detect statically; this linter focuses on the simple case of testing an expression against a literal value, e.g. `(1L, foo(x))` should be `(foo(x), 1L)`.

## Examples

```r
# will produce lints
lint(
  text = "expect_equal(2, x)",
  linters = yoda_test_linter()
)

lint(
  text = 'expect_identical("a", x)',
  linters = yoda_test_linter()
)

# okay
lint(
  text = "expect_equal(x, 2)",
  linters = yoda_test_linter()
)

lint(
  text = 'expect_identical(x, "a")',
  linters = yoda_test_linter()
)
```

## Further Reading

* [lintr - yoda_test_linter](https://lintr.r-lib.org/reference/yoda_test_linter.html)