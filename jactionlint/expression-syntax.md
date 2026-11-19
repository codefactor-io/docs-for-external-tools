Pattern: Invalid expression syntax

Issue: -

## Description

A ${{ }} expression has a syntax error.

The rule `expression-syntax` reports a `${{ }}` expression that does not parse: an invalid character, an operator that GitHub Actions does not have, a missing parenthesis or an expression that ends too early. The rule is in the `correctness` profile.

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
