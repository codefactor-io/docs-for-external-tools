Pattern: Typosquatting dependency

Issue: -

## Description

A dependency name is one or two edits (insertions, deletions, substitutions or adjacent swaps) away from a popular PyPI or npm package, with at most a third of the name changed. Typosquatted packages are a common supply-chain attack. Known legitimate look-alikes are allowlisted.


Example of **insecure** code:

```text
reqeusts==2.31.0
```

Example of **secure** code:

```text
requests==2.31.0
```

## Further Reading

* [PEP 503 - name normalization](https://peps.python.org/pep-0503/)
