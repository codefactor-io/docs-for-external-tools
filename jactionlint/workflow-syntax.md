Pattern: Invalid workflow syntax

Issue: -

## Description

A workflow uses an unexpected key or places a key where it is not supported. Keys are case-sensitive, so `Shell` is not the same as `shell`.

Correct misspelled keys and follow the GitHub Actions workflow structure.

## Examples

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    # ERROR: Typo of `defaults:`
    default:
      run:
        working-directory: /path/to/dir
    steps:
      - run: echo hello
        # ERROR: `shell:` must be in lower case
        Shell: bash
```

## Further Reading

* [jactionlint - Unexpected keys](https://jactionlint.jdx.dev/checks#check-unexpected-keys)
* [jactionlint - workflow-syntax](https://jactionlint.jdx.dev/rules#workflow-syntax)
