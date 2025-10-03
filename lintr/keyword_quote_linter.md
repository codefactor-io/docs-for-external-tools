Pattern: Unnecessary quoting in call

Issue: -

## Description

Any valid symbol can be used as a keyword argument to an R function call. Sometimes, it is necessary to quote (or backtick) an argument that is not an otherwise valid symbol (e.g. creating a vector whose names have spaces); besides this edge case, quoting should not be done.

## Examples

```r
# will produce lints
lint(
  text = 'data.frame("a" = 1)',
  linters = keyword_quote_linter()
)

lint(
  text = "data.frame(`a` = 1)",
  linters = keyword_quote_linter()
)

lint(
  text = 'my_list$"key"',
  linters = keyword_quote_linter()
)

lint(
  text = 's4obj@"key"',
  linters = keyword_quote_linter()
)

# okay
lint(
  text = "data.frame(`a b` = 1)",
  linters = keyword_quote_linter()
)

lint(
  text = "my_list$`a b`",
  linters = keyword_quote_linter()
)
```

## Further Reading

* [lintr - keyword_quote_linter](https://lintr.r-lib.org/reference/keyword_quote_linter.html)