Pattern: Invalid schedule time zone

Issue: -

## Description

A schedule's `timezone` is not a valid IANA time zone name. Use a recognized name, such as `Etc/UTC` or `America/New_York`.

## Examples

Example of **incorrect** code:

```yaml
on:
  schedule:
    - cron: '*/5 * * * *'
      timezone: Asia/Somewhere
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
```

Example of **correct** code:

```yaml
on:
  schedule:
    - cron: '*/5 * * * *'
      timezone: Etc/UTC
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
```

## Further Reading

* [jactionlint - CRON syntax and IANA timezone string at on.schedule](https://jactionlint.jdx.dev/checks#check-cron-syntax-and-timezone)
* [jactionlint - invalid-timezone](https://jactionlint.jdx.dev/rules#invalid-timezone)
