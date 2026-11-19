Pattern: Credentials persisted by `actions/checkout`

Issue: -

## Description

`actions/checkout` saves Git credentials on disk by default. Later steps can read them, and uploading files that contain them can expose the token.

Set `persist-credentials: false` unless later Git commands need authentication. Versions before v6 store the credentials in `.git/config`; v6 and later store them under `$RUNNER_TEMP`.

## Examples

Example of **incorrect** code:

```yaml
on: push

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v5
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
```

## Further Reading

* [zizmor - artipacked](https://docs.zizmor.sh/audits/#artipacked)
