Pattern: Unknown event

Issue: -

## Description

A workflow's `on` setting names an event that GitHub Actions does not recognize.

Correct the event name, such as using `pull_request` instead of `pullreq`.

## Examples

Example of **incorrect** code:

```yaml
on:
  pullreq:
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
```

Example of **correct** code:

```yaml
on:
  pull_request:
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
```

## Further Reading

* [jactionlint - Webhook events validation](https://jactionlint.jdx.dev/checks#check-webhook-events)
* [jactionlint - unknown-event](https://jactionlint.jdx.dev/rules#unknown-event)
