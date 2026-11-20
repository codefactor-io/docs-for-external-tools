Pattern: Use of `with` for async context manager

Issue: -

## Description

An asynchronous context manager is entered with `with` instead of `async with`. The regular statement expects synchronous context-manager methods and raises a `TypeError` when only asynchronous methods are available.

Use `async with` inside an asynchronous function.

## Examples

Example of **incorrect** code:

```python
from contextlib import asynccontextmanager


@asynccontextmanager
async def async_context():
    yield


with async_context():
    print("This will cause an error at runtime")
```

Example of **correct** code:

```python
from contextlib import asynccontextmanager


@asynccontextmanager
async def async_context():
    yield


async def main():
    async with async_context():
        print("This works correctly")
```

## Further Reading

* [Pylint - async-context-manager-with-regular-with](https://pylint.readthedocs.io/en/latest/user_guide/messages/error/async-context-manager-with-regular-with.html)
