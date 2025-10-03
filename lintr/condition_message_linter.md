Pattern: Malformed use of `paste()`/`paste0()`

Issue: -

## Description

This linter discourages combining condition functions like `stop()` with string concatenation functions `paste()` and `paste0()`. This is because

    `stop(paste0(...))` is redundant as it is exactly equivalent to `stop(...)`

    `stop(paste(...))` is similarly equivalent to `stop(...`) with separators

The same applies to the other default condition functions as well, i.e., `warning()`, `message()`, and `packageStartupMessage()`.


## Examples

```r
# will produce lints
lint(
  text = 'stop(paste("a string", "another"))',
  linters = condition_message_linter()
)

lint(
  text = 'warning(paste0("a string", " another"))',
  linters = condition_message_linter()
)

# okay
lint(
  text = 'stop("a string", " another")',
  linters = condition_message_linter()
)

lint(
  text = 'warning("a string", " another")',
  linters = condition_message_linter()
)

lint(
  text = 'warning(paste("a string", "another", sep = "-"))',
  linters = condition_message_linter()
)
```

## Further Reading

* [lintr - condition_message_linter](https://lintr.r-lib.org/reference/condition_message_linter.html)