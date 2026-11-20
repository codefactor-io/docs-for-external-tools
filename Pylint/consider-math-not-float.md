Pattern: Use of `float()` instead of `math` constant

Issue: -

## Description

Creating infinity or NaN with `float("inf")` or `float("nan")` converts a string at runtime. The constants `math.inf` and `math.nan` express the intended values directly and avoid repeated string conversion.

Use the corresponding constant from `math` instead.

## Examples

Example of **incorrect** code:

```python
infinity = float("inf")
```

Example of **correct** code:

```python
import math

infinity = math.inf
```

## Further Reading

* [Pylint - consider-math-not-float](https://pylint.readthedocs.io/en/latest/user_guide/messages/refactor/consider-math-not-float.html)
