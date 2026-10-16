Pattern: Reflective dangerous call

Issue: -

## Description

A Python script reaches an execution sink indirectly: `getattr(obj, "exec")`-style access with a literal or joined-string name of `exec`, `eval`, `system`, `popen` or `__import__`, or a lookup through `module.__dict__`. Reflection like this is used to hide dangerous calls from review.


Example of **insecure** code:

```python
import os

run = getattr(os, "sys" + "tem")
run(cmd)
```

Example of **secure** code:

```python
import subprocess

subprocess.run(["git", "status"], check=True)
```

## Further Reading

* [CWE-94: Improper Control of Generation of Code](https://cwe.mitre.org/data/definitions/94.html)
