Pattern: Runtime compile() call

Issue: -

## Description

A Python script calls the builtin `compile()` to build a code object from a string at runtime. Combined with `exec()`/`eval()` this is a common obfuscation step. `re.compile` is not reported.


Example of **insecure** code:

```python
code = compile(source, "<plugin>", "exec")
exec(code)
```

Example of **secure** code:

```python
# Ship the code as a normal module and import it.
```

## Further Reading

* [Python docs - compile()](https://docs.python.org/3/library/functions.html#compile)
* [CWE-94: Improper Control of Generation of Code](https://cwe.mitre.org/data/definitions/94.html)
