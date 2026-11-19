Pattern: Untrusted input in script

Issue: -

## Description

A script embeds untrusted input through a `${{ ... }}` expression. GitHub Actions substitutes the value before the script runs, so input such as an issue title can become executable shell code.

Pass the value through an environment variable and quote the shell variable when using it. Do not interpolate the environment variable back into the script with `${{ ... }}`.

## Examples

Example of **incorrect** code:

```yaml
on:
  issues:
    types: [opened]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Check title
        run: echo "${{ github.event.issue.title }}"
```

Example of **correct** code:

```yaml
on:
  issues:
    types: [opened]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Check title
        run: echo "$ISSUE_TITLE"
        env:
          ISSUE_TITLE: ${{ github.event.issue.title }}
```

## Further Reading

* [zizmor - template-injection](https://docs.zizmor.sh/audits/#template-injection)
