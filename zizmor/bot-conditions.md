Pattern: Spoofable bot actor check

Issue: -

## Description

A condition uses `github.actor` to identify a trusted bot. This value identifies the actor associated with the triggering activity, not necessarily the author of the pull request. A bot's involvement does not make the rest of the branch trustworthy.

For checks that depend on who opened a pull request, use `github.event.pull_request.user.login` instead.

## Examples

Example of **incorrect** code:

```yaml
on: pull_request

jobs:
  test:
    runs-on: ubuntu-latest
    if: github.actor == 'dependabot[bot]'
    steps:
      - run: echo 'Pull request opened by Dependabot'
```

Example of **correct** code:

```yaml
on: pull_request

jobs:
  test:
    runs-on: ubuntu-latest
    if: github.event.pull_request.user.login == 'dependabot[bot]'
    steps:
      - run: echo 'Pull request opened by Dependabot'
```

## Further Reading

* [zizmor - bot-conditions](https://docs.zizmor.sh/audits/#bot-conditions)
