Pattern: Duplicate step ID

Issue: -

## Description

A step ID is not unique within its job.

The rule `duplicate-step-id` reports a step ID that is not unique within its job. A job ID that is defined twice is reported as `duplicate-key`.

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo 'hello'
        id: step_id
      - run: echo 'bye'
        # ERROR: Duplicate step ID
        id: STEP_ID
  # ERROR: Duplicate job ID
  TEST:
    runs-on: ubuntu-latest
    steps:
      - run: echo 'hello'
        # OK. Step ID uniqueness is job-local
        id: step_id
```

## Further Reading

* [jactionlint - Job ID and step ID uniqueness](https://jactionlint.jdx.dev/checks#check-job-step-ids)
* [jactionlint - duplicate-step-id](https://jactionlint.jdx.dev/rules#duplicate-step-id)
