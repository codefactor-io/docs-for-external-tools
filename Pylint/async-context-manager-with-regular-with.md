Pattern: Async context manager used with regular with

Issue: -

## Description

Used when an async context manager is used with a regular 'with' statement instead of 'async with'.

Example of **incorrect** code:

```python
from contextlib import asynccontextmanager


@asynccontextmanager
async def async_context():
    yield


with async_context():  # [async-context-manager-with-regular-with]
    print("This will cause an error at runtime")
```

Example of **correct** code:

```python
import asyncio
from contextlib import asynccontextmanager


@asynccontextmanager
async def async_context():
    yield


async def main():
    async with async_context():
        print("This works correctly")
```
