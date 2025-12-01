Pattern: Use of `print()` for logging

Issue: -

## Description

The default print method for character vectors is appropriate for interactively inspecting objects, not for logging messages. Thus checked-in usage like `print(paste('Data has', nrow(DF), 'rows.'))` is better served by using `cat()`, e.g. `cat(sprintf('Data has %d rows.\n', nrow(DF)))` (noting that using `cat()` entails supplying your own line returns, and that `glue::glue()` might be preferable to `sprintf()` for constructing templated strings).

Lastly, note that `message()` differs slightly from `cat()` in that it prints to `stderr` by default, not `stdout`, but is still a good option to consider for logging purposes.

## Examples

```r
# will produce lints
lint(
  text = "print('a')",
  linters = print_linter()
)

lint(
  text = "print(paste(x, 'y'))",
  linters = print_linter()
)

# okay
lint(
  text = "print(x)",
  linters = print_linter()
)
```

## Further Reading

* [lintr - print_linter](https://lintr.r-lib.org/reference/print_linter.html)