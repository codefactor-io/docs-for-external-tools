Pattern: Dangerous workflow trigger

Issue: -

## Description

Triggers such as `pull_request_target`, `workflow_run`, and `issue_comment` run in the target repository's context and can be influenced by untrusted users. Checking out or executing attacker-controlled code in that context can expose repository secrets or write permissions.

Use `pull_request` for ordinary pull request checks. If a privileged trigger is necessary, keep untrusted code and inputs away from privileged operations.

## Examples

Example of **incorrect** code:

```yaml
on: pull_request_target

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v5
        with:
          ref: ${{ github.event.pull_request.head.sha }}
      - run: make test
```

Example of **correct** code:

```yaml
on: pull_request

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v5
      - run: make test
```

## Further Reading

* [zizmor - dangerous-triggers](https://docs.zizmor.sh/audits/#dangerous-triggers)
