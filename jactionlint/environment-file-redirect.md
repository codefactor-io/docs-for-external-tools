Pattern: Broken environment file write

Issue: -

## Description

A script writes to GITHUB_OUTPUT or another environment file of the runner without the $, or empties it with > after it wrote to it.

The rule `environment-file-redirect` reports a script that writes to `GITHUB_OUTPUT` or to another environment file of the runner in a way that loses data: without the `$` in front of the name, or with a `>` that empties the file after the script already wrote to it.

Example of **incorrect** code:

```yaml
on: push

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      # ERROR: without a $ this writes a file named GITHUB_OUTPUT in the working directory
      - id: version
        run: echo "version=1.2.3" >> GITHUB_OUTPUT
      # ERROR: the second > empties the file, so "a" is lost
      - id: pair
        run: |
          echo "a=1" >> "$GITHUB_OUTPUT"
          echo "b=2" > "$GITHUB_OUTPUT"
      # OK: the variable, appended
      - run: echo "c=3" >> "$GITHUB_OUTPUT"
      # OK: each step has its own file, so a lone > is harmless
      - run: echo "d=4" > "$GITHUB_OUTPUT"
```

## Further Reading

* [jactionlint - Writes to the environment files that lose data](https://jactionlint.jdx.dev/checks#check-environment-file-redirect)
* [jactionlint - environment-file-redirect](https://jactionlint.jdx.dev/rules#environment-file-redirect)
