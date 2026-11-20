Pattern: Impossible comparison

Issue: -

## Description

A condition combines comparisons that contradict each other, such as `a > b and b > a`. The condition can never be true, so any code that depends on it will not run.

Remove or correct the contradictory comparison to express the intended condition.

## Examples

Example of **incorrect** code:

```python
def has_more_apples_than_bananas(apples, bananas):
    # The two checks contradict each other: if there are more apples than
    # bananas, there cannot also be more bananas than apples.
    return apples > bananas and bananas > apples
```

Example of **correct** code:

```python
def has_more_apples_than_bananas(apples, bananas):
    return apples > bananas
```

## Further Reading

* [Pylint - impossible-comparison](https://pylint.readthedocs.io/en/latest/user_guide/messages/refactor/impossible-comparison.html)
