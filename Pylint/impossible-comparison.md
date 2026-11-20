Pattern: Impossible comparison

Issue: -

## Description

Emitted when a boolean condition contains a chain of comparisons that is logically contradictory and can never be true (e.g. `a > b and b > a`).

Example of **incorrect** code:

```python
def has_more_apples_than_bananas(apples, bananas):
    # The two checks contradict each other: if there are more apples than
    # bananas, there cannot also be more bananas than apples.
    return apples > bananas and bananas > apples  # [impossible-comparison]
```

Example of **correct** code:

```python
def has_more_apples_than_bananas(apples, bananas):
    return apples > bananas
```
