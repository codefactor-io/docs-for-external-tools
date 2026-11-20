Pattern: Chained comparison can be simplified to equality

Issue: -

## Description

Emitted when the operands of a boolean condition form a cycle of weak inequalities (`<=` or `>=`). The condition is equivalent to checking that all the operands are equal.

Example of **incorrect** code:

```python
def baskets_hold_the_same(red, green):
    # Each basket holds at least as many apples as the other, so the two
    # baskets hold the same number.
    return red >= green and green >= red  # [chained-comparison-all-equal]
```

Example of **correct** code:

```python
def baskets_hold_the_same(red, green):
    return red == green
```
