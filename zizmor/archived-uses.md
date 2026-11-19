Pattern: Action from archived repository

Issue: -

## Description

An action or reusable workflow comes from an archived repository that no longer gets fixes.

Unmaintained repositories are more likely to accumulate indirect vulnerabilties, including in any dependencies that have been vendored into JavaScript actions (or that are used indirectly through transitive dependencies that have gone stale).

Example of **incorrect** code:

```yaml
- uses: actions/create-release@v1
```

Example of **correct** code:

```yaml
- run: gh release create "$GITHUB_REF_NAME"
  env:
    GH_TOKEN: ${{ github.token }}
```

## Further Reading

* [zizmor - archived-uses](https://docs.zizmor.sh/audits/#archived-uses)
