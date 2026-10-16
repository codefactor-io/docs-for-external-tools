Pattern: Shipped Python bytecode

Issue: -

## Description

The skill ships compiled Python bytecode (a `__pycache__` directory or `.pyc`/`.pyo` files). Bytecode can't be reviewed like source and may differ from the source next to it.


Example of **insecure** code:

```text
my-skill/scripts/__pycache__/run.cpython-312.pyc
```

Example of **secure** code:

```text
my-skill/scripts/run.py
```
