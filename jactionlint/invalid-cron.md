Pattern: Invalid cron schedule

Issue: -

## Description

A scheduled workflow has an invalid cron expression. GitHub Actions expects five fields describing the minute, hour, day of the month, month, and day of the week.

Use a valid five-field cron expression.

## Examples

Example of **incorrect** code:

```yaml
on:
  schedule:
    - cron: '0 */3 * *'
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
    - cron: '0 */3 * * *'
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
```

## Further Reading

* [jactionlint - CRON syntax and IANA timezone string at on.schedule](https://jactionlint.jdx.dev/checks#check-cron-syntax-and-timezone)
* [jactionlint - invalid-cron](https://jactionlint.jdx.dev/rules#invalid-cron)
