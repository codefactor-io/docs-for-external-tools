Pattern: Invalid expression syntax

Issue: -

## Description

A GitHub Actions expression inside `${{ }}` contains invalid syntax, such as an unsupported operator, an invalid string delimiter, or a missing closing parenthesis.

Use the supported expression syntax and single quotes for string literals.

## Examples

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      # " is not available for string literal delimiter
      - run: echo '${{ "hello" }}'
      # + operator does not exist
      - run: echo '${{ 1 + 1 }}'
      # Missing ')' paren
      - run: echo "${{ toJson(hashFiles('**/lock', '**/cache/') }}"
      # unexpected end of input
      - run: echo '${{ github.event. }}'
```

## Further Reading

* [jactionlint - Syntax check for expression ${{ }}](https://jactionlint.jdx.dev/checks#check-syntax-expression)
* [jactionlint - expression-syntax](https://jactionlint.jdx.dev/rules#expression-syntax)
