Pattern: `return` shadowed by `finally` clause

Issue: -

## Description

Emitted when a `return` statement is found in a `finally` block. This will overwrite the return value of a function and should be avoided.

Example of **incorrect** code:

```python
def second_favorite():
    fruits = ["kiwi", "pineapple"]
    try:
        return fruits[1]
    finally:
        # because of this `return` statement, this function will always return "kiwi"
        return fruits[0]  # [return-in-finally]
```

Example of **correct** code:

```python
def second_favorite():
    fruits = ["kiwi", "pineapple"]
    try:
        return fruits[1]
    except KeyError:
        ...

    return fruits[0]
```
