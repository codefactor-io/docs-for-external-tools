Pattern: Wrong reusable workflow input type

Issue: -

## Description

The type of a value passed to a reusable workflow does not match its input.

| Rule | Reports |
| --- | --- |
| `invalid-workflow-call-input` | an input of `on.workflow_call` whose default value does not fit its type, or that is required and has a default value |
| `invalid-workflow-call` | a call whose `uses:` does not follow the format of a reusable workflow |
| `invalid-local-workflow` | a called workflow of the repository that does not exist, cannot be parsed or has no `workflow_call` event |
| `missing-workflow-input`, `missing-workflow-secret` | a call that does not pass a required input or secret |
| `unknown-workflow-input`, `unknown-workflow-secret` | a call that passes an input or secret which the called workflow does not define |
| `workflow-input-type` | a value passed to an input of another type |
| `workflow-call-permissions` | a called job that needs permissions which the calling job does not grant |

Example of **incorrect** code:

```yaml
on:
  workflow_call:
    inputs:
      scheme:
        description: Scheme of URL
        # OK: Type is string
        default: https
        type: string
      host:
        default: example.com
        type: string
      port:
        description: Port of URL
        # ERROR: Type is number but default value is string
        default: ':1234'
        type: number
      query:
        description: Query of URL
        # ERROR: Type must be one of number, string, boolean
        type: object
      path:
        description: Path of URL
        required: true
        # ERROR: Default value is never used since this input is required
        default: ''
        type: string
jobs:
  do:
    runs-on: ubuntu-latest
    steps:
      - run: echo "${{ inputs.scheme }}://${{ inputs.host }}:${{ inputs.port }}${{ inputs.path }}"
```

## Further Reading

* [jactionlint - Reusable workflows](https://jactionlint.jdx.dev/checks#check-reusable-workflows)
* [jactionlint - workflow-input-type](https://jactionlint.jdx.dev/rules#workflow-input-type)
