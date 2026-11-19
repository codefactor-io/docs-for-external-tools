Pattern: Unpinned tool version

Issue: -

## Description

An action is configured so that it installs the latest version of its external tool at runtime.

When using one of the known actions, set `with.version` to a specific tool version instead of relying on default versions or `latest`.

Example of **incorrect** code:

```yaml
- uses: extractions/setup-just@v3
```

Example of **correct** code:

```yaml
- uses: extractions/setup-just@v3
  with:
    just-version: 1.43.0
```

## Further Reading

* [zizmor - unpinned-tools](https://docs.zizmor.sh/audits/#unpinned-tools)
