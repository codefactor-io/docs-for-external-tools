Pattern: Decoded or downloaded code execution

Issue: -

## Description

`exec()` or `eval()` runs code that was just decoded, downloaded or produced by another dangerous call: the first argument contains a call to `compile`, `__import__`, `os.*`, `subprocess.*`, or a `base64`, `codecs`, `marshal`, `urllib`, `requests` or `httpx` function. This is the classic shape of a dropper.


Example of **insecure** code:

```python
import base64

exec(base64.b64decode(PAYLOAD))
```

Example of **secure** code:

```python
# Ship readable code; never execute decoded or downloaded content.
```

## Further Reading

* [CWE-94: Improper Control of Generation of Code](https://cwe.mitre.org/data/definitions/94.html)
