Pattern: Always-true `if` condition

Issue: -

## Description

An `if` condition contains text or whitespace outside its `${{ ... }}` expression. GitHub Actions treats the result as a nonempty string, which is true even when the expression evaluates to `false`.

For example, YAML's `|` block scalar adds a trailing newline outside the expression. Write the condition without `${{ ... }}` to avoid this problem.

## Examples

Example of **incorrect** code:

```yaml
on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    if: |
      ${{ github.event_name == 'push' }}
    steps:
      - run: echo 'Only on push'
```

Example of **correct** code:

```yaml
on: [push, pull_request]

jobs:
  test:
    runs-on: ubuntu-latest
    if: github.event_name == 'push'
    steps:
      - run: echo 'Only on push'
```

## Further Reading

* [zizmor - unsound-condition](https://docs.zizmor.sh/audits/#unsound-condition)
