Pattern: Malformed expression delimiters

Issue: -

## Description

A value looks like a GitHub Actions expression but uses incorrect delimiters, such as `${ github.ref }` or `$ {{ github.sha }}`. GitHub expands expressions only inside `${{ }}`.

Use the correct delimiters. With the `pedantic` option, this rule also checks shell-style variables in action inputs.

## Examples

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
