Pattern: Use of `==`/`!=` on logical vector

Issue: -

## Description

Testing `x == TRUE` is redundant if `x` is a logical vector. Wherever this is used to improve readability, the solution should instead be to improve the naming of the object to better indicate that its contents are logical. This can be done using prefixes (is, has, can, etc.). For example, `is_child`, `has_parent_supervision`, `can_watch_horror_movie` clarify their logical nature, while `child`, `parent_supervision`, `watch_horror_movie` don't.

## Examples

```r
# will produce lints
lint(
  text = "if (any(x == TRUE)) 1",
  linters = redundant_equals_linter()
)
#> <text>:1:9: warning: [redundant_equals_linter] Using == on a logical vector is redundant. Well-named logical vectors can be used directly in filtering. For data.table's `i` argument, wrap the column name in (), like `DT[(is_treatment)]`.
#> if (any(x == TRUE)) 1
#>  


# okay
lint(
  text = "if (any(x)) 1",
  linters = redundant_equals_linter()
)
#> ℹ No lints found.
```

## Further Reading

* [lintr - redundant_equals_linter](https://lintr.r-lib.org/reference/redundant_equals_linter.html)