Pattern: Missing use of `nlevels(x)`

Issue: -

## Description

`length(levels(x))` is the same as `nlevels(x)`, but harder to read.

## Examples

```r
# will produce lints
lint(
  text = "length(levels(x))",
  linters = length_levels_linter()
)

# okay
lint(
  text = "length(c(levels(x), levels(y)))",
  linters = length_levels_linter()
)
```

## Further Reading

* [lintr - length_levels_linter](https://lintr.r-lib.org/reference/length_levels_linter.html)