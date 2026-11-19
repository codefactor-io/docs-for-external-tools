Pattern: Malformed expression delimiters

Issue: -

## Description

Text such as ${ github.ref }, $ {{ x }} or {{ github.sha }} is meant to be an expression but is not one. With the option pedantic, so is a shell variable in the input of an action.

The rule `malformed-expression-delimiters` reports text that is meant to be an expression but is not one, because GitHub expands only `${{ }}`: a dollar sign, two braces and no space in between. The rule is in the `correctness` profile, and its rule option `pedantic` adds a second tier.

Example of **incorrect** code:

```yaml
on: push

jobs:
  test:
    runs-on: ubuntu-latest
    env:
      # ERROR: one brace, GitHub does not expand it
      REF: ${ github.ref }
      # ERROR: a space after the dollar
      SHA: $ {{ github.sha }}
      # ERROR: no dollar
      TAG: v-{{ github.run_number }}
      # OK: these are not expressions
      TEMPLATE: "{{ .Values.image }}"
      HOME_BIN: ${HOME}/bin
    steps:
      - run: echo "${GITHUB_REF} {{ github.sha }}"
```

## Further Reading

* [jactionlint - Expressions written with the wrong delimiters](https://jactionlint.jdx.dev/checks#check-malformed-expression-delimiters)
* [jactionlint - malformed-expression-delimiters](https://jactionlint.jdx.dev/rules#malformed-expression-delimiters)
