Pattern: Missing required action input

Issue: -

## Description

A required input of an action is not specified.

The rules `missing-action-input` and `unknown-action-input` report a required input that a step does not set at `with:`, and an input that the action does not define. For an action of the same repository, jactionlint reads the `action.yml` file of the action. Both rules are in the `correctness` profile.

Example of **incorrect** code:

```yaml
# select: missing-action-input,unknown-action-input
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      # missing required input "message"
      - uses: ./.github/actions/my-action
      # unexpected input "additions"
      - uses: ./.github/actions/my-action
        with:
          name: rhysd
          message: hello
          additions: foo, bar
```

## Further Reading

* [jactionlint - Local action inputs validation at with:](https://jactionlint.jdx.dev/checks#check-local-action-inputs)
* [jactionlint - missing-action-input](https://jactionlint.jdx.dev/rules#missing-action-input)
