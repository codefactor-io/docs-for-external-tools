Pattern: Context not available here

Issue: -

## Description

A context or special function is used where it is not available.

The rule `context-availability` reports a context or a special function that is used at a key where GitHub Actions does not provide it.

Example of **incorrect** code:

```yaml
on: push

defaults:
  run:
    # ERROR: No context is available here
    shell: ${{ env.SHELL }}

jobs:
  test:
    strategy:
      matrix:
        directory:
          # OK: 'github' context is available here
          - ${{ github.workflow }}
          # ERROR: 'runner' context is not available here
          - ${{ runner.temp }}
    runs-on: ubuntu-latest
    defaults:
      run:
        # OK: 'env' context is available here
        shell: ${{ env.SHELL }}
    env:
      # ERROR: 'env' context is not available here
      FOO: ${{ env.BAR }}
    steps:
      - env:
          # OK: 'env' context is available here
          FOO: ${{ env.BAR }}
        # ERROR: No context is available here
        shell: ${{ env.SHELL}}
        # ERROR: 'success()' function is not available here
        run: echo 'Success? ${{ success() }}'
        # OK: 'success()' function is available here
        if: success()
```

## Further Reading

* [jactionlint - Availability of contexts and special functions](https://jactionlint.jdx.dev/checks#ctx-spfunc-availability)
* [jactionlint - context-availability](https://jactionlint.jdx.dev/rules#context-availability)
