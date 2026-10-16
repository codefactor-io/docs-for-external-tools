Pattern: Dynamic __import__() call

Issue: -

## Description

A Python script imports a module by a computed name with `__import__()`. Dynamic imports hide which code the skill loads, which defeats review and static analysis.


Example of **insecure** code:

```python
mod = __import__(config["module"])
```

Example of **secure** code:

```python
import json  # import what the skill needs explicitly
```

## Further Reading

* [Python docs - __import__()](https://docs.python.org/3/library/functions.html#import__)
