Pattern: Missing token for `gh` command

Issue: -

## Description

A `run` script uses the GitHub CLI command `gh` without an authentication token. GitHub-hosted runners include the CLI, but it is not authenticated automatically.

Set `GH_TOKEN`, `GITHUB_TOKEN`, `GH_ENTERPRISE_TOKEN`, or `GITHUB_ENTERPRISE_TOKEN` in the step, job, or workflow environment. Commands such as `gh --version` and `gh help` do not need a token.

## Examples

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: gh pr list --state open
```

Example of **correct** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: gh pr list --state open
        env:
          GH_TOKEN: ${{ github.token }}
```

## Further Reading

* [jactionlint - The gh command without a token](https://jactionlint.jdx.dev/checks#check-gh-without-token)
* [jactionlint - gh-without-token](https://jactionlint.jdx.dev/rules#gh-without-token)
