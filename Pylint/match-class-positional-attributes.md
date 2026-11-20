Pattern: Positional attributes in class pattern

Issue: -

## Description

Keyword attributes are more explicit and slightly faster since CPython can skip the `__match_args__` lookup.

Example of **incorrect** code:

```python
class Book:
    __match_args__ = ("title", "year")

    def __init__(self, title, year):
        self.title = title
        self.year = year


def func(item: Book):
    match item:
        case Book("abc", 2000):  # [match-class-positional-attributes]
            ...
```

Example of **correct** code:

```python
class Book:
    __match_args__ = ("title", "year")

    def __init__(self, title, year):
        self.title = title
        self.year = year


def func(item: Book):
    match item:
        case Book(title="abc", year=2000):
            ...
```
