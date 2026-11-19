Pattern: Typosquatted action

Issue: -

## Description

An action reference resembles a popular action but names a different owner or repository. For example, `action/checkout` is not `actions/checkout`. An attacker can register a misspelled name to run their code in workflows that use it.

Check the action's official repository and correct the `uses` reference.

## Examples

Example of **incorrect** code:

```yaml
on: push

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: action/checkout@v5
```

Example of **correct** code:

```yaml
on: push

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v5
```

## Further Reading

* [zizmor - typosquat-uses](https://docs.zizmor.sh/audits/#typosquat-uses)
