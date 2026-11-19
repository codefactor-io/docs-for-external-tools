Pattern: Unpinned tool version

Issue: -

## Description

An action installs an external tool without a specific version, or uses `latest`. Pinning the action itself does not pin a tool it downloads at runtime, so workflow behavior can change unexpectedly.

This rule checks `aquasecurity/setup-trivy` and `1password/load-secrets-action`. Set their `with.version` input to a specific tool version.

## Examples

Example of **incorrect** code:

```yaml
on: push

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: aquasecurity/setup-trivy@v0.2.6
```

Example of **correct** code:

```yaml
on: push

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: aquasecurity/setup-trivy@v0.2.6
        with:
          version: "0.58.2"
```

## Further Reading

* [zizmor - unpinned-tools](https://docs.zizmor.sh/audits/#unpinned-tools)
