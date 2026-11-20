Pattern: Comprehension unpacking in unsupported Python version

Issue: -

## Description

Unpacking with `*` or `**` in a comprehension requires Python 3.15 or later. This syntax is incompatible with a project whose Pylint `py-version` setting includes an older Python version.

Use a nested comprehension or an explicit loop for compatibility with older versions. Only change the target version if the project no longer needs to support those versions.

## Examples

For a project configured with `py-version=3.14`:

Example of **incorrect** code:

```python
baskets = [["apple", "banana"], ["cherry"]]
fruits = [*basket for basket in baskets]
```

Example of **correct** code:

```python
baskets = [["apple", "banana"], ["cherry"]]
fruits = [fruit for basket in baskets for fruit in basket]
```

## Further Reading

* [Pylint - using-comprehension-unpacking-in-unsupported-version](https://pylint.readthedocs.io/en/latest/user_guide/messages/warning/using-comprehension-unpacking-in-unsupported-version.html)
