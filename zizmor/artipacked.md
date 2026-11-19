Pattern: Credentials persisted by checkout

Issue: -

## Description

The git credentials of actions/checkout are kept on disk, where later steps or uploaded artifacts can leak them.

By default, using [actions/checkout](https://github.com/actions/checkout) causes a credential to be persisted on disk. Versions below v6.0.0 store the credential directly in the checked-out repo's `.git/config`, while v6.0.0 and later store it under `$RUNNER_TEMP`.

Example of **incorrect** code:

```yaml
- uses: actions/checkout@v5
- uses: actions/upload-artifact@v5
  with:
    path: .
```

Example of **correct** code:

```yaml
- uses: actions/checkout@v5
  with:
    persist-credentials: false
- uses: actions/upload-artifact@v5
  with:
    path: .
```

## Further Reading

* [zizmor - artipacked](https://docs.zizmor.sh/audits/#artipacked)
