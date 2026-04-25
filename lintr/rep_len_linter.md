Pattern: Missing use of `rep_len(x, n)`

Issue: -

## Description

`rep(x, length.out = n)` calls `rep_len(x, n)` "under the hood". The latter is thus more direct and equally readable.

## Examples

```r
# will produce lints
lint(
  text = "rep(1:3, length.out = 10)",
  linters = rep_len_linter()
)

# okay
lint(
  text = "rep_len(1:3, 10)",
  linters = rep_len_linter()
)

lint(
  text = "rep(1:3, each = 2L, length.out = 10L)",
  linters = rep_len_linter()
)
```

## Further Reading

* [lintr - rep_len_linter](https://lintr.r-lib.org/reference/rep_len_linter.html)