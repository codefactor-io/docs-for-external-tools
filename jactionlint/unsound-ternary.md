Pattern: Ternary idiom with falsy value

Issue: -

## Description

In the expression `cond && b || c`, a falsy value for `b` makes the result `c` even when `cond` is true. Falsy literals include `''`, `0`, `false`, and `null`.

Use an expression that preserves the intended result when the condition is true.

## Examples

Example of **incorrect** code:

```yaml
on: push
env:
  PREFIX: ${{ github.ref == 'refs/heads/main' && '' || 'staging-' }}
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
```

Example of **correct** code:

```yaml
on: push
env:
  PREFIX: ${{ github.ref != 'refs/heads/main' && 'staging-' || '' }}
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
```

## Further Reading

* [jactionlint - Falsy value in the a && b || c ternary idiom](https://jactionlint.jdx.dev/checks#check-falsy-ternary)
* [jactionlint - unsound-ternary](https://jactionlint.jdx.dev/rules#unsound-ternary)
