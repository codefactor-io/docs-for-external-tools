Pattern: Invalid `workflow_call` input

Issue: -

## Description

An input declared under `on.workflow_call.inputs` has a default value that does not match its type, or combines `required: true` with a default that will never be used.

Match the default value to the declared type, or remove the default from a required input.

## Examples

Example of **incorrect** code:

```yaml
on:
  workflow_call:
    inputs:
      retries:
        type: number
        default: many
      target:
        type: string
        required: true
        default: production
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
```

Example of **correct** code:

```yaml
on:
  workflow_call:
    inputs:
      retries:
        type: number
        default: 3
      target:
        type: string
        required: true
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
```

## Further Reading

* [jactionlint - Reusable workflows](https://jactionlint.jdx.dev/checks#check-reusable-workflows)
* [jactionlint - invalid-workflow-call-input](https://jactionlint.jdx.dev/rules#invalid-workflow-call-input)
