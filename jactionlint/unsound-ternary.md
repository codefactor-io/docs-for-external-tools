Pattern: Ternary idiom with falsy value

Issue: -

## Description

The a && b || c idiom has a falsy b so it always evaluates to c.

The rule `unsound-ternary` reports the idiom `cond && b || c` when `b` is a literal that is always falsy: `''`, `0`, `false` or `null`. The idiom is commonly used as a ternary operator, but it works only when `b` is truthy. Otherwise the result is always `c`.

Example of **incorrect** code:

```yaml
env:
  # Always evaluated to 'staging-' regardless of the condition
  PREFIX: ${{ env.DEPLOY == 'true' && '' || 'staging-' }}
```

## Further Reading

* [jactionlint - Falsy value in the a && b || c ternary idiom](https://jactionlint.jdx.dev/checks#check-falsy-ternary)
* [jactionlint - unsound-ternary](https://jactionlint.jdx.dev/rules#unsound-ternary)
