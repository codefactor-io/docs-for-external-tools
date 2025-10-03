Pattern: Poor usage of `paste()`

Issue: -

## Description

The following issues are linted by default by this linter  (see arguments for which can be de-activated optionally):

1. Block usage of `paste()` with `sep = ""`. `paste0()` is a faster, more concise alternative.
2. Block usage of `paste()` or `paste0()` with `collapse = ", "`. `toString()]` is a direct
   wrapper for this, and alternatives like `glue::glue_collapse()` might give better messages for humans.
3. Block usage of `paste0()` that supplies `sep=` -- this is not a formal argument to `paste0`, and
   is likely to be a mistake.
4. Block usage of `paste()` / `paste0()` combined with `rep()` that could be replaced by
   `strrep()`. `strrep()` can handle the task of building a block of repeated strings
   (e.g. often used to build "horizontal lines" for messages). This is both more readable and
   skips the (likely small) overhead of putting two strings into the global string cache when only one is needed.

   Only target scalar usages -- `strrep` can handle more complicated cases (e.g. `strrep(letters, 26:1)`,
   but those aren't as easily translated from a `paste(collapse=)` call.
   
## Examples

```r
# will produce lints
lint(
  text = 'paste("a", "b", sep = "")',
  linters = paste_linter()
)
#> <text>:1:1: warning: [paste_linter] paste0(...) is better than paste(..., sep = "").
#> paste("a", "b", sep = "")
#> ^~~~~~~~~~~~~~~~~~~~~~~~~


# okay
lint(
  text = 'paste0("a", "b")',
  linters = paste_linter()
)
#> ℹ No lints found.
```

## Further Reading

* [lintr - paste_linter](https://lintr.r-lib.org/reference/paste_linter.html)