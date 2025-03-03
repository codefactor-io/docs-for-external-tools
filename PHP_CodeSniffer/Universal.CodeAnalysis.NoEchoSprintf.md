Pattern: Use of `echo [v]sprintf(...);`

Issue: -

## Description

Detects use of the inefficient `echo [v]sprintf(...);` combi. Use `[v]printf()` instead.

## Further Reading

* [Universal.WhiteSpace.PrecisionAlignment](https://github.com/PHPCSStandards/PHPCSExtra?tab=readme-ov-file#universalcodeanalysisnoechosprintf-wrench-books)