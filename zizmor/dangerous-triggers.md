Pattern: Dangerous workflow trigger

Issue: -

## Description

The workflow uses a trigger such as pull_request_target, workflow_run or issue_comment that is very hard to use securely.

These triggers are dangerous because they run in the context of the target repository rather than the fork repository, while also being typically triggerable by the latter. This can lead to attacker controlled code execution or unexpected action runs with context controlled by a malicious fork.

Example of **incorrect** code:

```yaml
on: pull_request_target

jobs:
  build:
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
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v5
      - run: make test
```

## Further Reading

* [zizmor - dangerous-triggers](https://docs.zizmor.sh/audits/#dangerous-triggers)
