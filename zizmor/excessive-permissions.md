Pattern: Overly broad token permissions

Issue: -

## Description

A workflow or job grants `GITHUB_TOKEN` more permissions than it needs. If an action or script is compromised, those permissions increase the damage it can cause. Workflow-level permissions are inherited by jobs unless they override them.

Set workflow permissions to `{}` and grant only the required permissions to individual jobs.

## Examples

Example of **incorrect** code:

```yaml
on: push

permissions: write-all

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v5
      - run: make test
```

Example of **correct** code:

```yaml
on: push

permissions: {}

jobs:
  test:
    runs-on: ubuntu-latest
    permissions:
      contents: read
    steps:
      - uses: actions/checkout@v5
      - run: make test
```

## Further Reading

* [zizmor - excessive-permissions](https://docs.zizmor.sh/audits/#excessive-permissions)
