Pattern: Inconsistent pipe operator

Issue: -

## Description

Check that pipe operators are used consistently by file, or optionally specify one valid pipe operator.

## Examples

```r
# will produce lints
lint(
  text = "1:3 |> mean() %>% as.character()",
  linters = pipe_consistency_linter()
)

lint(
  text = "1:3 %>% mean() %>% as.character()",
  linters = pipe_consistency_linter("|>")
)

# okay
lint(
  text = "1:3 %>% mean() %>% as.character()",
  linters = pipe_consistency_linter()
)

lint(
  text = "1:3 |> mean() |> as.character()",
  linters = pipe_consistency_linter()
)

```

## Further Reading

* [lintr - pipe_consistency_linter](https://lintr.r-lib.org/reference/pipe_consistency_linter.html)