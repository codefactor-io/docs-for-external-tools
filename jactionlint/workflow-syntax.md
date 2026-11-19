Pattern: Invalid workflow syntax

Issue: -

## Description

The workflow does not follow the syntax of GitHub Actions workflows.

The rule `workflow-syntax` reports a key that the syntax of GitHub Actions workflows does not define in the mapping it appears in, such as a misspelled `defaults:` or a `Shell:` with a capital letter.

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
