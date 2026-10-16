Pattern: Dynamic eval() call

Issue: -

## Description

A Python script bundled with the skill calls the builtin `eval()`. `eval()` evaluates an arbitrary expression and is a common way to run attacker-controlled code. Use `ast.literal_eval()` for literals or an explicit parser.


Example of **insecure** code:

```python
settings = eval(open("settings.txt").read())
```

Example of **secure** code:

```python
import ast

settings = ast.literal_eval(open("settings.txt").read())
```

## Further Reading

* [Python docs - eval()](https://docs.python.org/3/library/functions.html#eval)
* [CWE-94: Improper Control of Generation of Code](https://cwe.mitre.org/data/definitions/94.html)
