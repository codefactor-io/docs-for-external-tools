Pattern: Unknown action input

Issue: -

## Description

An action receives an input that it does not declare. A misspelled input can leave the action using its default behavior instead of the intended value.

Check the action's metadata and correct or remove the input.

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
        with:
          message: Hello
          mesage: Hello
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
* [jactionlint - unknown-action-input](https://jactionlint.jdx.dev/rules#unknown-action-input)
