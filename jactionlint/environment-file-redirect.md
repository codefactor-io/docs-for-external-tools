Pattern: Incorrect environment file redirection

Issue: -

## Description

A script writes to a literal file named `GITHUB_OUTPUT` instead of the path in `$GITHUB_OUTPUT`, or overwrites an environment file after writing to it. Either mistake can lose outputs or other runner data.

Use the environment variable and append with `>>` when adding values.

## Examples

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo "version=1.2.3" >> GITHUB_OUTPUT
      - run: |
          echo "a=1" >> "$GITHUB_OUTPUT"
          echo "b=2" > "$GITHUB_OUTPUT"
```

Example of **correct** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo "version=1.2.3" >> "$GITHUB_OUTPUT"
      - run: |
          echo "a=1" >> "$GITHUB_OUTPUT"
          echo "b=2" >> "$GITHUB_OUTPUT"
```

## Further Reading

* [jactionlint - Writes to the environment files that lose data](https://jactionlint.jdx.dev/checks#check-environment-file-redirect)
* [jactionlint - environment-file-redirect](https://jactionlint.jdx.dev/rules#environment-file-redirect)
