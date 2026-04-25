Pattern: `stringsAsFactors` is not supplied explicitly

Issue: -

## Description

Designed for code bases written for versions of R before 4.0 seeking to upgrade to R >= 4.0, where one of the biggest pain points will surely be the flipping of the default value of `stringsAsFactors` from `TRUE` to `FALSE`.

## Examples

```r
# will produce lints
lint(
  text = 'data.frame(x = "a")',
  linters = strings_as_factors_linter()
)

# okay
lint(
  text = 'data.frame(x = "a", stringsAsFactors = TRUE)',
  linters = strings_as_factors_linter()
)

lint(
  text = 'data.frame(x = "a", stringsAsFactors = FALSE)',
  linters = strings_as_factors_linter()
)

lint(
  text = "data.frame(x = 1.2)",
  linters = strings_as_factors_linter()
)
```

## Further Reading

* [lintr - strings_as_factors_linter](https://lintr.r-lib.org/reference/strings_as_factors_linter.html)