Pattern: Bypassable `contains()` check

Issue: -

## Description

A condition uses `contains()` on a string to check whether a value is allowed. String matching accepts substrings, not just complete entries. A branch named `mai`, for example, matches the string `refs/heads/main refs/heads/develop`.

Use `contains()` with an array to check for an exact match instead.

## Examples

Example of **incorrect** code:

```yaml
on: push

jobs:
  test:
    runs-on: ubuntu-latest
    if: contains('refs/heads/main refs/heads/develop', github.ref)
    steps:
      - run: echo 'Allowed branch'
```

Example of **correct** code:

```yaml
on: push

jobs:
  test:
    runs-on: ubuntu-latest
    if: contains(fromJSON('["refs/heads/main", "refs/heads/develop"]'), github.ref)
    steps:
      - run: echo 'Allowed branch'
```

## Further Reading

* [zizmor - unsound-contains](https://docs.zizmor.sh/audits/#unsound-contains)
