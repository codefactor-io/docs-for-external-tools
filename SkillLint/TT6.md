Pattern: Untrusted data to deserializer flow

Issue: -

## Description

Network, user or file data flows into an insecure deserializer (pickle family, `marshal`, `dill`, `jsonpickle`, `joblib`, `pandas.read_pickle`, `yaml.unsafe_load`). Unpickling untrusted data runs arbitrary code.


Example of **insecure** code:

```python
import pickle, requests

model = pickle.loads(requests.get(MODEL_URL).content)
```

Example of **secure** code:

```python
import json, requests

config = json.loads(requests.get(CONFIG_URL).text)
```

## Further Reading

* [Python docs - pickle security warning](https://docs.python.org/3/library/pickle.html)
* [CWE-502: Deserialization of Untrusted Data](https://cwe.mitre.org/data/definitions/502.html)
