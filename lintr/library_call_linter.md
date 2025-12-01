Pattern: Malformed `library()` call

Issue: -

## Description

This linter covers several rules related to `library()` calls:

    Enforce such calls to all be at the top of the script.

    Block usage of argument `character.only`, in particular for loading packages in a loop.

    Block consecutive calls to `suppressMessages(library(.))` in favor of using `suppressMessages()` only once to suppress messages from all `library()` calls. Ditto `suppressPackageStartupMessages()`.


## Examples

```r
# will produce lints

code <- "library(dplyr)\nprint('test')\nlibrary(tidyr)"
writeLines(code)
lint(
  text = code,
  linters = library_call_linter()
)

lint(
  text = "library('dplyr', character.only = TRUE)",
  linters = library_call_linter()
)

code <- paste(
  "pkg <- c('dplyr', 'tibble')",
  "sapply(pkg, library, character.only = TRUE)",
  sep = "\n"
)
writeLines(code)
lint(
  text = code,
  linters = library_call_linter()
)

code <- "suppressMessages(library(dplyr))\nsuppressMessages(library(tidyr))"
writeLines(code)
lint(
  text = code,
  linters = library_call_linter()
)

# okay
code <- "library(dplyr)\nprint('test')"
writeLines(code)
lint(
  text = code,
  linters = library_call_linter()
)

code <- "# comment\nlibrary(dplyr)"
lint(
  text = code,
  linters = library_call_linter()
)

code <- paste(
  "foo <- function(pkg) {",
  "  sapply(pkg, library, character.only = TRUE)",
  "}",
  sep = "\n"
)
writeLines(code)
lint(
  text = code,
  linters = library_call_linter()
)

code <- "suppressMessages({\n  library(dplyr)\n  library(tidyr)\n})"
writeLines(code)
lint(
  text = code,
  linters = library_call_linter()
)


```

## Further Reading

* [lintr - library_call_linter](https://lintr.r-lib.org/reference/library_call_linter.html)