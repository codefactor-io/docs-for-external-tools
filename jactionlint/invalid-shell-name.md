Pattern: Invalid shell name

Issue: -

## Description

A `shell` setting names a shell that GitHub Actions does not provide on the job's runner. This also applies to `defaults.run.shell`.

Choose a supported shell for that operating system, or provide a custom shell command containing the `{0}` script placeholder.

## Examples

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
        # ERROR: 'sh' is not available on Windows
        shell: sh
      - run: echo 'hello'
        # OK: 'powershell' is only available on Windows
        shell: powershell
```

## Further Reading

* [jactionlint - Shell name validation at shell:](https://jactionlint.jdx.dev/checks#check-shell-names)
* [jactionlint - invalid-shell-name](https://jactionlint.jdx.dev/rules#invalid-shell-name)
