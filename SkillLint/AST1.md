Pattern: Dynamic exec() call

Issue: -

## Description

A Python script bundled with the skill calls the builtin `exec()`. `exec()` runs arbitrary code from a string, so whatever reaches it (a downloaded payload, a decoded blob, user input) runs with the agent's privileges. Calls are resolved through import aliases, so `from builtins import exec as run; run(code)` is also reported.


Example of **insecure** code:

```python
code = fetch_plugin()
exec(code)
```

Example of **secure** code:

```python
import importlib

plugin = importlib.import_module("plugins." + validated_name)
plugin.run()
```

## Further Reading

* [Python docs - exec()](https://docs.python.org/3/library/functions.html#exec)
* [CWE-94: Improper Control of Generation of Code](https://cwe.mitre.org/data/definitions/94.html)
