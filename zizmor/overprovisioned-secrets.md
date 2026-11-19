Pattern: Exposure of entire `secrets` context

Issue: -

## Description

A workflow passes the entire `secrets` context to the runner, for example with `toJSON(secrets)`. This exposes secrets that the step does not need and increases the impact of a compromised action or script.

Reference only the individual secrets needed by the step.

## Examples

Example of **incorrect** code:

```yaml
on: push

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v5
        with:
          persist-credentials: false
      - run: ./deploy.sh
        env:
          SECRETS: ${{ toJSON(secrets) }}
```

Example of **correct** code:

```yaml
on: push

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v5
        with:
          persist-credentials: false
      - run: ./deploy.sh
        env:
          DEPLOY_TOKEN: ${{ secrets.DEPLOY_TOKEN }}
```

## Further Reading

* [zizmor - overprovisioned-secrets](https://docs.zizmor.sh/audits/#overprovisioned-secrets)
