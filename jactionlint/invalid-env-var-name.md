Pattern: Invalid environment variable name

Issue: -

## Description

An environment variable name under `env` contains `=`, `&`, a space, or a tab. Rename the variable and update its references.

## Examples

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    env:
      FOO=BAR: foo
      FOO BAR: foo
    steps:
      - run: echo 'hello'
```

## Further Reading

* [jactionlint - Environment variable names](https://jactionlint.jdx.dev/checks#check-env-var-names)
* [jactionlint - invalid-env-var-name](https://jactionlint.jdx.dev/rules#invalid-env-var-name)
