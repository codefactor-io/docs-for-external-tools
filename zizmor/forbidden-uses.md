Pattern: Use of forbidden action

Issue: -

## Description

A repository-based `uses` reference violates the repository's configured allowlist or denylist. This rule is opt-in: it has no effect until `forbidden-uses` is configured in `zizmor.yml`.

Replace the action with an allowed alternative, or update the policy if the action has been approved.

## Examples

With the following `zizmor.yml`, only actions owned by `actions` are allowed:

```yaml
rules:
  forbidden-uses:
    config:
      allow:
        - actions/*
```

Example of **incorrect** code:

```yaml
on: push

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: some-org/untrusted-action@v1
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

* [zizmor - forbidden-uses](https://docs.zizmor.sh/audits/#forbidden-uses)
