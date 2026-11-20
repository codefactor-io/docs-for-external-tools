Pattern: Break in finally block

Issue: -

## Description

Emitted when the `break` keyword is found inside a finally clause. This will raise a SyntaxWarning starting in Python 3.14.

Example of **incorrect** code:

```python
while True:
    try:
        pass
    finally:
        break  # [break-in-finally]
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
