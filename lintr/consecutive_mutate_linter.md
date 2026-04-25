Pattern: Consecutive calls to `mutate()`

Issue: -

## Description

`dplyr::mutate()` accepts any number of columns, so sequences like `DF %>% dplyr::mutate(..1) %>% dplyr::mutate(..2)` are redundant – they can always be expressed with a single call to `dplyr::mutate()`.

## Examples

```r
# will produce lints
lint(
  text = "x %>% mutate(a = 1) %>% mutate(b = 2)",
  linters = consecutive_mutate_linter()
)

# okay
lint(
  text = "x %>% mutate(a = 1, b = 2)",
  linters = consecutive_mutate_linter()
)

code <- "library(dbplyr)\nx %>% mutate(a = 1) %>% mutate(a = a + 1)"
writeLines(code)
lint(
  text = code,
  linters = consecutive_mutate_linter()
)
```

## Further Reading

* [lintr - consecutive_mutate_linter](https://lintr.r-lib.org/reference/consecutive_mutate_linter.html)