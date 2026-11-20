Pattern: Inequality checks instead of equality

Issue: -

## Description

Comparisons such as `a >= b and b >= a` require both values to be equal. A cycle of `<=` or `>=` comparisons between several values has the same effect.

Use equality comparisons to express this intent directly.

## Examples

Example of **incorrect** code:

```python
def baskets_hold_the_same(red, green):
    # Each basket holds at least as many apples as the other, so the two
    # baskets hold the same number.
    return red >= green and green >= red
```

Example of **correct** code:

```python
def baskets_hold_the_same(red, green):
    return red == green
```

## Further Reading

* [Pylint - chained-comparison-all-equal](https://pylint.readthedocs.io/en/latest/user_guide/messages/refactor/chained-comparison-all-equal.html)
