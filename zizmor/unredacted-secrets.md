Pattern: Secret value not reliably redacted

Issue: -

## Description

A workflow extracts part of a secret, such as a field from a JSON value. GitHub Actions masks the complete stored secret, but it may not recognize the extracted value in logs.

Store sensitive values as separate secrets and reference them directly so the runner can mask their exact values.

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
          PASSWORD: ${{ fromJSON(secrets.CREDENTIALS).password }}
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
          PASSWORD: ${{ secrets.PASSWORD }}
```

## Further Reading

* [zizmor - unredacted-secrets](https://docs.zizmor.sh/audits/#unredacted-secrets)
