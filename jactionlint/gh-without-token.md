Pattern: gh command without token

Issue: -

## Description

A script runs the gh command although no GH_TOKEN or GITHUB_TOKEN reaches the step, so gh stops.

The rule `gh-without-token` reports a `run:` script that runs the `gh` command of GitHub CLI although no token reaches the step, so that `gh` stops. The GitHub-hosted runners have the GitHub CLI installed, but it is not logged in. It stops with `gh: To use GitHub CLI in a GitHub Actions workflow, set the GH_TOKEN environment variable` unless one of `GH_TOKEN`, `GITHUB_TOKEN`, `GH_ENTERPRISE_TOKEN` or `GITHUB_ENTERPRISE_TOKEN` is in its environment.

Example of **incorrect** code:

```yaml
on: push

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      # ERROR: gh stops because neither GH_TOKEN nor GITHUB_TOKEN is set
      - run: gh pr list --state open
      # OK: the token is set for the step
      - run: gh pr list --state open
        env:
          GH_TOKEN: ${{ github.token }}
      # OK: gh --version and gh help need no token
      - run: gh --version
```

## Further Reading

* [jactionlint - The gh command without a token](https://jactionlint.jdx.dev/checks#check-gh-without-token)
* [jactionlint - gh-without-token](https://jactionlint.jdx.dev/rules#gh-without-token)
