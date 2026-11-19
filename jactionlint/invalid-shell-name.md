Pattern: Invalid shell name

Issue: -

## Description

A shell name is not available on the runner.

The rule `invalid-shell-name` reports a `shell:` value that is not one of the shells that GitHub provides on the runner of the job. It checks the `shell:` of a step and the `shell:` of `defaults.run` at the job and at the workflow level.

Example of **incorrect** code:

```yaml
on: push
jobs:
  linux:
    runs-on: ubuntu-latest
    steps:
      - run: echo 'hello'
        # ERROR: Unavailable shell
        shell: dash
      - run: echo 'hello'
        # ERROR: 'powershell' is only available on Windows
        shell: powershell
  mac:
    runs-on: macos-latest
    defaults:
      run:
        # ERROR: default config is also checked. fish is not supported
        shell: fish
    steps:
      - run: echo 'hello'
        # OK: Custom shell
        shell: 'perl {0}'
  windows:
    runs-on: windows-latest
    steps:
      - run: echo 'hello'
        # ERROR: 'sh' is only available on Windows
        shell: sh
      - run: echo 'hello'
        # OK: 'powershell' is only available on Windows
        shell: powershell
```

## Further Reading

* [jactionlint - Shell name validation at shell:](https://jactionlint.jdx.dev/checks#check-shell-names)
* [jactionlint - invalid-shell-name](https://jactionlint.jdx.dev/rules#invalid-shell-name)
