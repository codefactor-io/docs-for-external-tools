Pattern: Schedule too frequent

Issue: -

## Description

A scheduled job runs more often than once every 5 minutes.

The rules `invalid-cron`, `cron-too-frequent` and `invalid-timezone` report a `schedule` trigger that GitHub cannot run as written: a cron expression that is not valid, a job that would run more often than once every 5 minutes, and a `timezone` that is not an IANA timezone name.

Example of **incorrect** code:

```yaml
on:
  schedule:
    # ERROR: Cron syntax is not correct
    - cron: '0 */3 * *'
    # ERROR: Interval of scheduled job is too small (job runs too frequently)
    - cron: '* */3 * * *'
    # ERROR: Timezone is not a valid IANA timezone string
    - cron: '*/5 * * * *'
      timezone: 'Asia/Somewhere'

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo ...
```

## Further Reading

* [jactionlint - CRON syntax and IANA timezone string at on.schedule](https://jactionlint.jdx.dev/checks#check-cron-syntax-and-timezone)
* [jactionlint - cron-too-frequent](https://jactionlint.jdx.dev/rules#cron-too-frequent)
