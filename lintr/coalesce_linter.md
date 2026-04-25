Pattern: Missing use of `x %||% y`

Issue: -

## Description

The `x %||% y` is equivalent to `if (is.null(x)) y else x`, but more expressive. It is exported by R since 4.4.0, and equivalents have been available in other tidyverse packages for much longer, e.g. 2008 for ggplot2.


## Examples

```r
# will produce lints
lint(
  text = "if (is.null(x)) y else x",
  linters = coalesce_linter()
)

lint(
  text = "if (!is.null(x)) x else y",
  linters = coalesce_linter()
)

lint(
  text = "if (is.null(x[1])) x[2] else x[1]",
  linters = coalesce_linter()
)

# okay
lint(
  text = "x %||% y",
  linters = coalesce_linter()
)

lint(
  text = "x %||% y",
  linters = coalesce_linter()
)

lint(
  text = "x[1] %||% x[2]",
  linters = coalesce_linter()
)
```

## Further Reading

* [lintr - coalesce_linter](https://lintr.r-lib.org/reference/coalesce_linter.html)