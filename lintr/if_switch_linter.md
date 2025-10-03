Pattern: Missing use of `switch()`

Issue: -

## Description

`switch()` statements in R are used to delegate behavior based on the value of some input scalar string, e.g. `switch(x, a = 1, b = 3, c = 7, d = 8)` will be one of 1, 3, 7, or 8, depending on the value of `x`.


## Examples

```r
# will produce lints
lint(
  text = "if (x == 'a') 1 else if (x == 'b') 2 else 3",
  linters = if_switch_linter()
)

# okay
lint(
  text = "switch(x, a = 1, b = 2, 3)",
  linters = if_switch_linter()
)
#> ℹ No lints found.
```

## Further Reading

* [lintr - if_switch_linter](https://lintr.r-lib.org/reference/if_switch_linter.html)