Pattern: Missing use of `nzchar()`

Issue: -

## Description

`nzchar()` efficiently determines which of a vector of strings are empty (i.e., are `""`). It should in most cases be used instead of constructions like `string == ""` or `nchar(string) == 0`.

## Examples

```r
# will produce lints
lint(
  text = "x[x == '']",
  linters = nzchar_linter()
)

lint(
  text = "x[nchar(x) > 0]",
  linters = nzchar_linter()
)

# okay
lint(
  text = "x[!nzchar(x, keepNA = TRUE)]",
  linters = nzchar_linter()
)

lint(
  text = "x[nzchar(x, keepNA = TRUE)]",
  linters = nzchar_linter()
)
```

## Further Reading

* [lintr - nzchar_linter](https://lintr.r-lib.org/reference/nzchar_linter.html)