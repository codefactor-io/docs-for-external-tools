Pattern: Duplicate arguments in function call

Issue: -

## Description

Duplicate-named objects are hard to work with programmatically and should typically be avoided.

Some cases are run-time errors (e.g. `mean(x = 1:5, x = 2:3)`), otherwise this linter is used to discourage explicitly providing duplicate names to objects (e.g. `c(a = 1, a = 2)`). 


## Further Reading

* [lintr - Duplicate argument linter](https://lintr.r-lib.org/reference/duplicate_argument_linter.html)