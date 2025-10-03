Pattern: Use of `if (!A) x else y`

Issue: -

## Description

`if (!A) x else y` is the same as `if (A) y else x`, but the latter is easier to reason about in the else case. The former requires double negation that can be avoided by switching the statement order.

## Examples

```r
# will produce lints
lint(
  text = "if (!A) x else y",
  linters = if_not_else_linter()
)

lint(
  text = "if (!A) x else if (!B) y else z",
  linters = if_not_else_linter()
)

lint(
  text = "ifelse(!is_treatment, x, y)",
  linters = if_not_else_linter()
)

lint(
  text = "if (!is.null(x)) x else 2",
  linters = if_not_else_linter(exceptions = character())
)

# okay
lint(
  text = "if (A) x else y",
  linters = if_not_else_linter()
)

lint(
  text = "if (!A) x else if (B) z else y",
  linters = if_not_else_linter()
)

lint(
  text = "ifelse(is_treatment, y, x)",
  linters = if_not_else_linter()
)

lint(
  text = "if (!is.null(x)) x else 2",
  linters = if_not_else_linter()
)
```

## Further Reading

* [lintr - if_not_else_linter](https://lintr.r-lib.org/reference/if_not_else_linter.html)