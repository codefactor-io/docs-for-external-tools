Pattern: Deprecated action input

Issue: -

## Description

A deprecated input of an action is used.

The rule `deprecated-action-input` reports an input that a step sets at `with:` and that the action marks as deprecated with [`deprecationMessage`](https://docs.github.com/en/actions/reference/workflows-and-actions/metadata-syntax#inputsinput_iddeprecationmessage). It is in the `correctness` profile and reports `error`.

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
