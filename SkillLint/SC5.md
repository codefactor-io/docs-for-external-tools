Pattern: Abandoned dependency

Issue: -

## Description

A dependency in a requirements file, `setup.py`, `Pipfile`, `pyproject.toml`, `uv.lock`, `poetry.lock`, `package.json` or an npm lockfile is on a list of known abandoned packages (for example `pycrypto`, `nose`, `request`, `optimist`). Abandoned packages no longer receive security fixes.


Example of **insecure** code:

```text
pycrypto==2.6.1
```

Example of **secure** code:

```text
pycryptodome==3.20.0
```
