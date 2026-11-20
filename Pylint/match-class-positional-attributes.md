Pattern: Positional attributes in class pattern

Issue: -

## Description

A class pattern matches attributes by position, relying on the order defined in `__match_args__`. Keyword patterns make it clear which attributes are being checked and avoid the positional attribute lookup.

Name the attributes explicitly, for example `Book(title="abc", year=2000)` instead of `Book("abc", 2000)`.

## Examples

Example of **incorrect** code:

```python
class Book:
    __match_args__ = ("title", "year")

    def __init__(self, title, year):
        self.title = title
        self.year = year


def func(item: Book):
    match item:
        case Book("abc", 2000):
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

## Further Reading

* [Pylint - match-class-positional-attributes](https://pylint.readthedocs.io/en/latest/user_guide/messages/refactor/match-class-positional-attributes.html)
