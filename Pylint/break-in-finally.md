Pattern: Use of `break` in `finally` block

Issue: -

## Description

A `break` that exits a `finally` block can discard a pending exception or override an earlier return. This can hide failures and make control flow difficult to follow. Python 3.14 and later emit a `SyntaxWarning` for this construct.

Move the `break` outside the `finally` block so cleanup does not suppress exceptions.

## Examples

Example of **incorrect** code:

```python
while True:
    try:
        pass
    finally:
        break
```

Example of **correct** code:

```python
while True:
    try:
        pass
    except ValueError:
        pass
    else:
        break
```

## Further Reading

* [Pylint - break-in-finally](https://pylint.readthedocs.io/en/latest/user_guide/messages/warning/break-in-finally.html)
