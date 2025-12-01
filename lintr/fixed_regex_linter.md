Pattern: Missing `fixed=TRUE` for regular expression

Issue: -

## Description

Invoking a regular expression engine is overkill for cases when the search pattern only involves static patterns.

## Examples

```r
# will produce lints
code_lines <- 'gsub("\\\\.", "", x)'
writeLines(code_lines)
lint(
  text = code_lines,
  linters = fixed_regex_linter()
)

lint(
  text = 'grepl("a[*]b", x)',
  linters = fixed_regex_linter()
)

lint(
  text = 'grepl("a[*]b", x)',
  linters = fixed_regex_linter(allow_unescaped = TRUE)
)

code_lines <- 'stringr::str_subset(x, "\\\\$")'
writeLines(code_lines)
lint(
  text = code_lines,
  linters = fixed_regex_linter()
)

lint(
  text = 'grepl("Munich", address)',
  linters = fixed_regex_linter()
)

# okay
code_lines <- 'gsub("\\\\.", "", x, fixed = TRUE)'
writeLines(code_lines)
lint(
  text = code_lines,
  linters = fixed_regex_linter()
)

lint(
  text = 'grepl("a*b", x, fixed = TRUE)',
  linters = fixed_regex_linter()
)

lint(
  text = 'stringr::str_subset(x, stringr::fixed("$"))',
  linters = fixed_regex_linter()
)

lint(
  text = 'grepl("Munich", address, fixed = TRUE)',
  linters = fixed_regex_linter()
)

lint(
  text = 'grepl("Munich", address)',
  linters = fixed_regex_linter(allow_unescaped = TRUE)
)
```

## Further Reading

* [lintr - fixed_regex_linter](https://lintr.r-lib.org/reference/fixed_regex_linter.html)