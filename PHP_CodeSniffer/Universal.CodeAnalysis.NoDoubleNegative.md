Pattern: Double negation

Issue: -

## Description

Detects double negation `!!` in code, which is effectively the same as a boolean cast, but with a much higher cognitive load.
Also detects triple negation `!!!`, which is effectively the same as a single negation.


## Further Reading

* [Universal.CodeAnalysis.NoDoubleNegative](https://github.com/PHPCSStandards/PHPCSExtra?tab=readme-ov-file#universal)