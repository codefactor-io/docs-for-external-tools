Pattern: Unused import

Issue: -

## Description

Check that imported packages are actually used.

## Examples

```r
# will produce lints
code_lines <- "library(dplyr)\n1 + 1"
writeLines(code_lines)
lint(
  text = code_lines,
  linters = unused_import_linter()
)

code_lines <- "library(dplyr)\ndplyr::tibble(a = 1)"
writeLines(code_lines)
lint(
  text = code_lines,
  linters = unused_import_linter()
)

# okay
code_lines <- "library(dplyr)\ntibble(a = 1)"
writeLines(code_lines)
lint(
  text = code_lines,
  linters = unused_import_linter()
)

code_lines <- "library(dplyr)\ndplyr::tibble(a = 1)"
writeLines(code_lines)
lint(
  text = code_lines,
  linters = unused_import_linter(allow_ns_usage = TRUE)
)
```

## Further Reading

* [lintr - unused_import_linter](https://lintr.r-lib.org/reference/unused_import_linter.html)