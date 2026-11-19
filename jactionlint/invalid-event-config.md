Pattern: Invalid event configuration

Issue: -

## Description

An event is configured with options it does not support. For example, `workflow_run` requires a `workflows` list, and other events cannot use that list.

Use only the configuration options supported by the selected event.

## Examples

Example of **incorrect** code:

```yaml
on:
  push:
    workflows: [Build]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
```

Example of **correct** code:

```yaml
on:
  push:
    branches: [main]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
```

## Further Reading

* [jactionlint - Webhook events validation](https://jactionlint.jdx.dev/checks#check-webhook-events)
* [jactionlint - invalid-event-config](https://jactionlint.jdx.dev/rules#invalid-event-config)
