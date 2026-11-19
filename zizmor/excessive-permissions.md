Pattern: Overly broad permissions

Issue: -

## Description

The workflow or a job grants broader GITHUB_TOKEN permissions than it needs.

Users frequently over-scope their workflow and job permissions, or set broad workflow-level permissions without realizing that all jobs inherit those permissions.

Example of **incorrect** code:

```yaml
on: push

permissions: write-all

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - run: make build
  test:
    runs-on: ubuntu-latest
    steps:
      - run: make test
```

Example of **correct** code:

```yaml
on: push

permissions:
  contents: read

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - run: make build
  test:
    runs-on: ubuntu-latest
    steps:
      - run: make test
```

## Further Reading

* [zizmor - excessive-permissions](https://docs.zizmor.sh/audits/#excessive-permissions)
