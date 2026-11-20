Pattern: Consider using math constant instead of float

Issue: -

## Description

Using math.inf or math.nan permits to benefit from typing and it is up to 4 times faster than a float call (after the initial import of math). This check also catches typos in float calls as a side effect.

Example of **incorrect** code:

```python
swag = float("inf")  # [consider-math-not-float]
```

Example of **correct** code:

```python
import math

swag = math.inf
```
