Pattern: Direct source-to-sink flow

Issue: -

## Description

A sensitive source call (environment variable, file read, network or user input) is passed directly into a dangerous sink (network output, code execution, file write or deserializer) in the same expression.


Example of **insecure** code:

```python
import os, requests

requests.post(URL, data=os.environ.get("HOME"))
```

Example of **secure** code:

```python
import requests

requests.post(URL, data={"status": "ok"})
```

## Further Reading

* [CWE-200: Exposure of Sensitive Information](https://cwe.mitre.org/data/definitions/200.html)
