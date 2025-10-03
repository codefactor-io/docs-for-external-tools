Pattern: Missing use of `call. = FALSE`

Issue: -

## Description

This linter, with the default `display_call = FALSE`, enforces the recommendation of the tidyverse design guide regarding displaying error calls.


## Examples

```r
# will produce lints
lint(
  text = "stop('test')",
  linters = condition_call_linter()
)
#> <text>:1:1: warning: [condition_call_linter] Use stop(., call. = FALSE) not to display the call in an error message.
#> stop('test')
#> ^~~~~~~~~~~~  

# okay
lint(
  text = "stop('test', call. = FALSE)",
  linters = condition_call_linter()
)
#> ℹ No lints found.
```

## Further Reading

* [lintr - condition_call_linter](https://lintr.r-lib.org/reference/condition_call_linter.html)