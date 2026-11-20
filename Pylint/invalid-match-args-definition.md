Pattern: Invalid __match_args__ definition

Issue: -

## Description

Emitted if `__match_args__` isn't a tuple of strings required for match.

Example of **incorrect** code:

```python
class Book:
    __match_args__ = ["title", "year"]  # [invalid-match-args-definition]

    def __init__(self, title, year):
        self.title = title
        self.year = year
```

Example of **correct** code:

```python
class Book:
    __match_args__ = ("title", "year")

    def __init__(self, title, year):
        self.title = title
        self.year = year
```
