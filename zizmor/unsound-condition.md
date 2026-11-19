Pattern: Always-true if condition

Issue: -

## Description

An if: condition is always true because of the characters around ${{ }}.

This happens because YAML's "block" scalars include a trailing newline by default, which is left outside of the GitHub Actions expression. This results in an expansion like `'false\n'` instead of `'false'`, which GitHub Actions interprets as a truthy value.

Example of **incorrect** code:

```yaml
if: |
  ${{ github.event_name == 'push' }}
```

Example of **correct** code:

```yaml
if: github.event_name == 'push'
```

## Further Reading

* [zizmor - unsound-condition](https://docs.zizmor.sh/audits/#unsound-condition)
