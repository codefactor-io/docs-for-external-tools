Pattern: Invalid environment variable name

Issue: -

## Description

An environment variable name contains characters which are not allowed.

The rule `invalid-env-var-name` reports an environment variable name under `env:` that contains `=`, `&`, a space or a tab.

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
