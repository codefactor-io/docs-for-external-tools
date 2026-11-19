Pattern: Deprecated action input

Issue: -

## Description

An action input is marked as deprecated in the action's metadata. The action's `deprecationMessage` explains which input or behavior to use instead.

Replace the deprecated input with the supported alternative.

## Examples

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: reviewdog/action-actionlint@v1
        with:
          # ERROR: Using a deprecated input
          fail_on_error: true
```

## Further Reading

* [jactionlint - Deprecated inputs usage](https://jactionlint.jdx.dev/checks#deprecated-inputs-usage)
* [jactionlint - deprecated-action-input](https://jactionlint.jdx.dev/rules#deprecated-action-input)
