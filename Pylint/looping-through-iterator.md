Pattern: Iterator consumed in nested loop

Issue: -

## Description

Used when an iterator defined in an outer loop scope is consumed in a nested loop. Because iterators are stateful and exhausted upon consumption, the inner loop will fully consume the iterator during the first iteration of the outer loop, leaving it empty for all subsequent iterations.

Example of **incorrect** code:

```python
# Looks like a tuple, but it is a generator: it can only be looped over once
fruits = (name.upper() for name in ["apple", "banana"])
for basket in ["red basket", "blue basket"]:
    for fruit in fruits:  # [looping-through-iterator]
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
