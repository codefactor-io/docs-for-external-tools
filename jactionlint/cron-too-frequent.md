Pattern: Overly frequent schedule

Issue: -

## Description

A scheduled workflow runs more often than once every five minutes, which GitHub Actions does not support.

Adjust the cron expression so runs are at least five minutes apart.

## Examples

Example of **incorrect** code:

```yaml
on:
  schedule:
    - cron: '* */3 * * *'
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
    - cron: '*/5 */3 * * *'
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
```

## Further Reading

* [jactionlint - CRON syntax and IANA timezone string at on.schedule](https://jactionlint.jdx.dev/checks#check-cron-syntax-and-timezone)
* [jactionlint - cron-too-frequent](https://jactionlint.jdx.dev/rules#cron-too-frequent)
