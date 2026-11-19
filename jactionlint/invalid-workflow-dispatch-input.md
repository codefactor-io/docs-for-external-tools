Pattern: Invalid `workflow_dispatch` input

Issue: -

## Description

An input under `on.workflow_dispatch.inputs` has an unsupported type, a `choice` input has no options, or a default value does not match the input's type or choices. Defining more than 25 inputs is also reported.

Use a supported type, provide options for choices, and choose a compatible default value.

## Examples

Example of **incorrect** code:

```yaml
on:
  workflow_dispatch:
    inputs:
      # Unknown input type
      id:
        type: text
      # ERROR: No options for 'choice' input type
      kind:
        type: choice
      name:
        type: choice
        options:
          - Tama
          - Mike
        # ERROR: Default value is not in options
        default: Chobi
      message:
        type: string
      verbose:
        type: boolean
        # ERROR: Boolean value must be 'true' or 'false'
        default: yes
      age:
        type: number
        # ERROR: Number value must be parsed as a float number
        default: teen

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      # ERROR: Undefined input
      - run: echo "${{ inputs.massage }}"
      # ERROR: Bool value is not available for object key
      - run: echo "${{ env[inputs.verbose] }}"
      # ERROR: Number value is not available for object key
      - run: echo "${{ env[inputs.age] }}"
      # ERROR: `github.event.inputs` is also not defined
      - run: echo "${{ github.event.inputs.massage }}"
```

## Further Reading

* [jactionlint - Workflow dispatch event validation](https://jactionlint.jdx.dev/checks#check-workflow-dispatch-events)
* [jactionlint - invalid-workflow-dispatch-input](https://jactionlint.jdx.dev/rules#invalid-workflow-dispatch-input)
