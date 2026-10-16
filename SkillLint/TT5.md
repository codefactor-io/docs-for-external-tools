Pattern: External input to execution flow

Issue: -

## Description

Network or user input flows into code execution (`exec`, `eval`, `compile`, `os.system`, `os.popen` or `subprocess`). This allows remote or injected code to run.


Example of **insecure** code:

```python
import requests

exec(requests.get(UPDATE_URL).text)
```

Example of **secure** code:

```python
# Ship code with the skill; treat downloaded content as data only.
```

## Further Reading

* [CWE-94: Improper Control of Generation of Code](https://cwe.mitre.org/data/definitions/94.html)
* [CWE-78: OS Command Injection](https://cwe.mitre.org/data/definitions/78.html)
