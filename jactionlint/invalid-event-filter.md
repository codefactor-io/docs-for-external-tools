Pattern: Invalid event filter

Issue: -

## Description

An event uses an unsupported filter or a pair of conflicting filters. For example, `paths` and `paths-ignore` cannot both be set for the same event.

Use filters supported by the event and choose one of each conflicting pair.

## Examples

Example of **incorrect** code:

```yaml
on:
  push:
    paths: ['src/**']
    paths-ignore: ['src/docs/**']
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
    paths:
      - 'src/**'
      - '!src/docs/**'
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
```

## Further Reading

* [jactionlint - Webhook events validation](https://jactionlint.jdx.dev/checks#check-webhook-events)
* [jactionlint - invalid-event-filter](https://jactionlint.jdx.dev/rules#invalid-event-filter)
