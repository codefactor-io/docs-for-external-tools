Pattern: Invalid activity type

Issue: -

## Description

An activity type is not available for the Webhook event.

The rules `unknown-event`, `invalid-activity-type`, `invalid-event-filter` and `invalid-event-config` report webhook events under `on:` that GitHub cannot use: an event that does not exist, an activity type or a filter that the event does not have, filters that exclude each other, and an event configured with options it does not support.

Example of **incorrect** code:

```yaml
on:
  push:
    # ERROR: Incorrect filter. 'branches' is correct
    branch: foo
    # ERROR: Both 'paths' and 'paths-ignore' filters cannot be used for the same event
    paths: path/to/foo
    paths-ignore: path/to/foo
  issues:
    # ERROR: Incorrect type. 'opened' is correct
    types: created
  release:
    # ERROR: 'tags' filter is not available for 'release' event
    tags: v*.*.*
  # ERROR: Unknown event name
  pullreq:

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo ...
```

## Further Reading

* [jactionlint - Webhook events validation](https://jactionlint.jdx.dev/checks#check-webhook-events)
* [jactionlint - invalid-activity-type](https://jactionlint.jdx.dev/rules#invalid-activity-type)
