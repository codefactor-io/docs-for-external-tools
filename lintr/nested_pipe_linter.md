Pattern: Use of nested pipe

Issue: -

## Description

Nesting pipes harms readability; extract sub-steps to separate variables, append further pipeline steps, or otherwise refactor such usage away.

## Examples

```r
# will produce lints
code <- "df1 %>%\n  inner_join(df2 %>%\n    select(a, b)\n  )"
writeLines(code)
lint(
  text = code,
  linters = nested_pipe_linter()
)

lint(
  text = "df1 %>% inner_join(df2 %>% select(a, b))",
  linters = nested_pipe_linter(allow_inline = FALSE)
)

lint(
  text = "tryCatch(x %>% filter(grp == 'a'), error = identity)",
  linters = nested_pipe_linter(allow_outer_calls = character())
)

# okay
lint(
  text = "df1 %>% inner_join(df2 %>% select(a, b))",
  linters = nested_pipe_linter()
)

code <- "df1 %>%\n  inner_join(df2 %>%\n    select(a, b)\n  )"
writeLines(code)
lint(
  text = code,
  linters = nested_pipe_linter(allow_outer_calls = "inner_join")
)

lint(
  text = "tryCatch(x %>% filter(grp == 'a'), error = identity)",
  linters = nested_pipe_linter()
)
```

## Further Reading

* [lintr - nested_pipe_linter](https://lintr.r-lib.org/reference/nested_pipe_linter.html)