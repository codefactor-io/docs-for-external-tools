Pattern: Too many positional sub-patterns

Issue: -

## Description

A class pattern supplies more positional sub-patterns than the class's `__match_args__` tuple allows. Python cannot map the extra positions to attributes and raises a `TypeError`.

Use keyword patterns for additional attributes, or remove the extra positional patterns.

## Examples

Example of **incorrect** code:

```python
class Book:
    __match_args__ = ("title", "year")

    def __init__(self, title, year, author):
        self.title = title
        self.year = year
        self.author = author


def func(item: Book):
    match item:
        case Book("title", 2000, "author"):
            ...
```

Example of **correct** code:

```python
class Book:
    __match_args__ = ("title", "year")

    def __init__(self, title, year, author):
        self.title = title
        self.year = year
        self.author = author


def func(item: Book):
    match item:
        case Book("title", 2000, author="author"):
            ...
```

## Further Reading

* [Pylint - too-many-positional-sub-patterns](https://pylint.readthedocs.io/en/latest/user_guide/messages/error/too-many-positional-sub-patterns.html)
