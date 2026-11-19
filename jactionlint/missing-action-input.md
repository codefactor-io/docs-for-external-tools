Pattern: Missing required action input

Issue: -

## Description

An action is called without a required input. Required inputs are declared in the action's metadata.

Provide the input under the step's `with` setting.

## Examples

Local action metadata:

```yaml
# file: .github/actions/greet/action.yml
name: Greet
description: Print a greeting
inputs:
  message:
    description: Greeting to print
    required: true
runs:
  using: composite
  steps:
    - run: echo "$MESSAGE"
      shell: bash
      env:
        MESSAGE: ${{ inputs.message }}
```

Example of **incorrect** code:

```yaml
# file: .github/workflows/ci.yml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: ./.github/actions/greet
```

Example of **correct** code:

```yaml
# file: .github/workflows/ci.yml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: ./.github/actions/greet
        with:
          message: Hello
```

## Further Reading

* [jactionlint - Local action inputs validation at with:](https://jactionlint.jdx.dev/checks#check-local-action-inputs)
* [jactionlint - missing-action-input](https://jactionlint.jdx.dev/rules#missing-action-input)
