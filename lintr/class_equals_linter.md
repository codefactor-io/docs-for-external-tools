Pattern: Block comparison of class with `==`

Issue: -

## Description

Usage like `class(x) == "character"` is prone to error since class in R is in general a vector. The correct version for S3 classes is `inherits()`: `inherits(x, "character")`. Often, class `k` will have an `is.` equivalent, for example `is.character()` or `is.data.frame()`.

## Examples

```r
# will produce lints
lint(
  text = 'is_lm <- class(x) == "lm"',
  linters = class_equals_linter()
)

lint(
  text = 'if ("lm" %in% class(x)) is_lm <- TRUE',
  linters = class_equals_linter()
)

# okay
lint(
  text = 'is_lm <- inherits(x, "lm")',
  linters = class_equals_linter()
)

lint(
  text = 'if (inherits(x, "lm")) is_lm <- TRUE',
  linters = class_equals_linter()
)
```

## Further Reading

* [lintr - class_equals_linter](https://lintr.r-lib.org/reference/class_equals_linter.html)