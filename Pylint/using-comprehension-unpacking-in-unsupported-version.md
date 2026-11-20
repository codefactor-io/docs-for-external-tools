Pattern: Comprehension unpacking used in unsupported Python version

Issue: -

## Description

Used when the py-version set by the user is lower than 3.15 and pylint encounters the `*` or `**` unpacking added by PEP 798 in a comprehension.

Example of **incorrect** code:

```python
baskets = [["apple", "banana"], ["cherry"]]
fruits = [*basket for basket in baskets]  # [using-comprehension-unpacking-in-unsupported-version]
```

Example of **correct** code:

```python
baskets = [["apple", "banana"], ["cherry"]]
fruits = [fruit for basket in baskets for fruit in basket]
```
