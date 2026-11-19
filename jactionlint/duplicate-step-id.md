Pattern: Duplicate step ID

Issue: -

## Description

Two steps in the same job use the same ID. Step IDs are compared without regard to case, so `step_id` and `STEP_ID` conflict.

Use a unique ID for each step within a job. The same ID can be used in a different job.

## Examples

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - id: step_id
        run: echo hello
      - id: STEP_ID
        run: echo goodbye
```

Example of **correct** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - id: hello
        run: echo hello
      - id: goodbye
        run: echo goodbye
```

## Further Reading

* [jactionlint - Job ID and step ID uniqueness](https://jactionlint.jdx.dev/checks#check-job-step-ids)
* [jactionlint - duplicate-step-id](https://jactionlint.jdx.dev/rules#duplicate-step-id)
