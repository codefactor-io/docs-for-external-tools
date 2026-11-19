Pattern: Recursive YAML alias

Issue: -

## Description

A YAML alias refers to its own anchor, directly or through another alias. This creates a recursive value that GitHub Actions cannot use.

Remove the circular reference and use an alias only for a value that does not contain itself.

## Examples

Example of **incorrect** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - &recursive
        run: echo hello
        env: *recursive
```

Example of **correct** code:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo hello
        env: &variables
          MESSAGE: hello
      - run: echo "$MESSAGE"
        env: *variables
```

## Further Reading

* [jactionlint - YAML anchors](https://jactionlint.jdx.dev/checks#yaml-anchors)
* [jactionlint - recursive-alias](https://jactionlint.jdx.dev/rules#recursive-alias)
