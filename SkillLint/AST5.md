Pattern: Shell Command Execution

Issue: -

## Description

A Python script runs a shell command with `os.system`, `os.popen`, the `os.exec*`/`os.spawn*` families or `os.posix_spawn`. These run with the full privileges of the agent process and are a direct path to command injection.


Example of **insecure** code:

```python
import os

os.system("tar xzf " + archive)
```

Example of **secure** code:

```python
import tarfile

with tarfile.open(archive) as tar:
    tar.extractall(path=target, filter="data")
```

## Further Reading

* [CWE-78: OS Command Injection](https://cwe.mitre.org/data/definitions/78.html)
