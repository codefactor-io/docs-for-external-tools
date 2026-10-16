Pattern: Variable-mediated taint flow

Issue: -

## Description

Data from a sensitive source reaches a dangerous sink through variables, containers, f-strings or calls to functions defined in the same file. The flow is tracked across scopes within one file.


Example of **insecure** code:

```python
import os, subprocess

flags = os.getenv("BUILD_FLAGS")
subprocess.run("make " + flags, shell=True)
```

Example of **secure** code:

```python
import shlex, subprocess

subprocess.run(["make", *shlex.split(ALLOWED_FLAGS)], check=True)
```

## Further Reading

* [CWE-200: Exposure of Sensitive Information](https://cwe.mitre.org/data/definitions/200.html)
