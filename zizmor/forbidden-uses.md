Pattern: Forbidden action

Issue: -

## Description

An action is used that the zizmor configuration of the repository forbids.

Type: `list`

Example of **incorrect** code:

```yaml
- uses: some-org/untrusted-action@v1
```

Example of **correct** code:

```yaml
- uses: actions/checkout@v5
```

## Further Reading

* [zizmor - forbidden-uses](https://docs.zizmor.sh/audits/#forbidden-uses)
