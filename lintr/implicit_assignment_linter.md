Pattern: Implicit assignment in function call

Issue: -

## Description

Assigning inside function calls makes the code difficult to read, and should be avoided, except for functions that capture side-effects (e.g. `capture.output()`).

## Examples

```r
# will produce lints
lint(
  text = "if (x <- 1L) TRUE",
  linters = implicit_assignment_linter()
)

lint(
  text = "mean(x <- 1:4)",
  linters = implicit_assignment_linter()
)

# okay
lines <- "x <- 1L\nif (x) TRUE"
writeLines(lines)
lint(
  text = lines,
  linters = implicit_assignment_linter()
)

lines <- "x <- 1:4\nmean(x)"
writeLines(lines)
lint(
  text = lines,
  linters = implicit_assignment_linter()
)

lint(
  text = "A && (B <- foo(A))",
  linters = implicit_assignment_linter(allow_lazy = TRUE)
)

lines <- c(
  "if (any(idx <- x < 0)) {",
  "  stop('negative elements: ', toString(which(idx)))",
  "}"
)
writeLines(lines)
lint(
  text = lines,
  linters = implicit_assignment_linter(allow_scoped = TRUE)
)
```

## Further Reading

* [lintr - implicit_assignment_linter](https://lintr.r-lib.org/reference/implicit_assignment_linter.html)