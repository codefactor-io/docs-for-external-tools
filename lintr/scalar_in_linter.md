Pattern: Misuse of `vector %in% set`

Issue: -

## Description

`vector %in% set` is appropriate for matching a vector to a set, but if that set has size 1, `==` is more appropriate.

## Examples

```r
# will produce lints
lint(
  text = "x %in% 1L",
  linters = scalar_in_linter()
)

lint(
  text = "x %chin% 'a'",
  linters = scalar_in_linter(in_operators = "%chin%")
)

# okay
lint(
  text = "x %in% 1:10",
  linters = scalar_in_linter()
)
```

## Further Reading

* [lintr - scalar_in_linter](https://lintr.r-lib.org/reference/scalar_in_linter.html)