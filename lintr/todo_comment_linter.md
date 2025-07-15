Pattern: Unresolved warning comment

Issue: -

## Description

Developers often add comments to code which is not complete or needs review. Most likely you want to fix or review the code, and then remove the comment, before you consider the code to be production ready.

Example of **incorrect** code:

```r
# FIXME: this is not a good idea
# TODO: need code review
arrange(value)
```

Example of **correct** code:

```r
# NOT READY FOR PRIME TIME
# but too bad, it is not a predefined warning term
arrange(value)
```

## Further Reading

* [lintr - Available linters](https://lintr.r-lib.org/reference/index.html)
