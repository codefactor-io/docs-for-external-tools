Pattern: Insecure Deserialization

Issue: -

## Description

A Python script loads data with an unsafe deserializer: `pickle`/`cPickle`/`marshal`/`dill` loads, `jsonpickle.decode`, `pandas.read_pickle`, `joblib.load`, `yaml.unsafe_load`, `yaml.load` without a safe loader, `torch.load` without `weights_only=True`, or `numpy.load(allow_pickle=True)`. Deserializing untrusted data with these runs arbitrary code.


Example of **insecure** code:

```python
import yaml

data = yaml.load(stream, Loader=yaml.Loader)
```

Example of **secure** code:

```python
import yaml

data = yaml.safe_load(stream)
```

## Further Reading

* [Python docs - pickle security warning](https://docs.python.org/3/library/pickle.html)
* [CWE-502: Deserialization of Untrusted Data](https://cwe.mitre.org/data/definitions/502.html)
