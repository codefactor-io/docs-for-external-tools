Pattern: Invalid filter pattern

Issue: -

## Description

A glob filter pattern is invalid.

The rule `invalid-glob` reports a filter pattern of `branches`, `branches-ignore`, `tags`, `tags-ignore`, `paths` or `paths-ignore` that GitHub cannot use: a glob with a syntax error, a character that a Git ref name cannot contain, or a path that starts with `.` or `..`.

Example of **incorrect** code:

```yaml
on:
  push:
    branches:
      # ^ is not available for branch name. This kind of mistake is usually caused by misunderstanding
      # that regular expression is available here
      - '^foo-'
    tags:
      # Invalid syntax. + cannot follow special character *
      - 'v*+'
      # Invalid character range 9-1
      - 'v[9-1]'
    paths:
      # GitHub Action's path filter doesn't recognize '.'
      - ./foo/bar.txt

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - run: echo ...
```

## Further Reading

* [jactionlint - Glob filter pattern syntax validation](https://jactionlint.jdx.dev/checks#check-glob-pattern)
* [jactionlint - invalid-glob](https://jactionlint.jdx.dev/rules#invalid-glob)
