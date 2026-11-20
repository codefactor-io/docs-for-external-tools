Pattern: Iterator consumed in nested loop

Issue: -

## Description

An inner loop reuses the same iterator across iterations of an outer loop. Iterators do not restart: once the inner loop consumes the remaining items, later iterations have nothing left to process.

Store the items in a list or tuple if they need to be visited repeatedly, or create a fresh iterator for each outer iteration.

## Examples

Example of **incorrect** code:

```python
# Looks like a tuple, but it is a generator: it can only be looped over once
fruits = (name.upper() for name in ["apple", "banana"])
for basket in ["red basket", "blue basket"]:
    for fruit in fruits:
        print(basket, fruit)
```

Example of **correct** code:

```python
# A real tuple: it can be looped over again and again
fruits = tuple(name.upper() for name in ["apple", "banana"])
for basket in ["red basket", "blue basket"]:
    for fruit in fruits:
        print(basket, fruit)
```

## Further Reading

* [Pylint - looping-through-iterator](https://pylint.readthedocs.io/en/latest/user_guide/messages/warning/looping-through-iterator.html)
