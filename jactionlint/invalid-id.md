Pattern: Invalid ID

Issue: -

## Description

A job or step ID does not follow the naming convention.

The rule `invalid-id` reports a job ID or a step ID that does not follow the naming convention, and a job ID listed in `needs:` that does not.

Example of **incorrect** code:

```yaml
on: push

jobs:
  # ERROR: '.' cannot be contained in ID
  foo-v1.2.3:
    runs-on: ubuntu-latest
    steps:
      - run: echo 'job ID with version'
        # ERROR: ID cannot contain spaces
        id: echo for test
  # ERROR: ID cannot start with '-'
  -hello-world-:
    runs-on: ubuntu-latest
    steps:
      - run: echo 'oops'
  # ERROR: ID cannot start with numbers
  2d-game:
    runs-on: ubuntu-latest
    steps:
      - run: echo 'oops'
```

## Further Reading

* [jactionlint - ID naming convention](https://jactionlint.jdx.dev/checks#id-naming-convention)
* [jactionlint - invalid-id](https://jactionlint.jdx.dev/rules#invalid-id)
