Pattern: Use of literal coercion

Issue: -

## Description

`as.integer(1)` (or `rlang::int(1)`) is the same as `1L` but the latter is more concise and gets typed correctly at compilation.

## Examples

```r
# will produce lints
lint(
  text = "int(1)",
  linters = literal_coercion_linter()
)

lint(
  text = "as.character(NA)",
  linters = literal_coercion_linter()
)

lint(
  text = "rlang::lgl(1L)",
  linters = literal_coercion_linter()
)

# okay
lint(
  text = "1L",
  linters = literal_coercion_linter()
)

lint(
  text = "NA_character_",
  linters = literal_coercion_linter()
)

lint(
  text = "TRUE",
  linters = literal_coercion_linter()
)
```

## Further Reading

* [lintr - literal_coercion_linter](https://lintr.r-lib.org/reference/literal_coercion_linter.html)