Pattern: Invalid activity type

Issue: -

## Description

An event lists an activity type that GitHub Actions does not support for that event. For example, the `issues` event supports `opened`, not `created`.

Choose an activity type supported by the event.

## Examples

Example of **incorrect** code:

```yaml
on:
  issues:
    types: [created]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
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
      - run: echo hello
```

## Further Reading

* [jactionlint - Webhook events validation](https://jactionlint.jdx.dev/checks#check-webhook-events)
* [jactionlint - invalid-activity-type](https://jactionlint.jdx.dev/rules#invalid-activity-type)
