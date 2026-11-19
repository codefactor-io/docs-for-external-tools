Pattern: Invalid permission

Issue: -

## Description

A permission scope or its value is invalid.

`invalid-permissions` reports a scope or an access level in `permissions:` that GitHub does not accept. `missing-permissions` reports a job that no `permissions:` covers, see [Require explicit permissions](https://jactionlint.jdx.dev/checks#require-explicit-permissions).

Example of **incorrect** code:

```yaml
on: push

# ERROR: Available values for whole permissions are "read-all", "write-all" or {}
permissions: write

jobs:
  test:
    runs-on: ubuntu-latest
    permissions:
      # ERROR: "checks" is correct scope name
      check: write
      # ERROR: Available values are "read", "write" or "none"
      issues: readable
      # ERROR: "models" doesn't have "write" scope
      models: write
    steps:
      - run: echo hello
```

## Further Reading

* [jactionlint - Permissions](https://jactionlint.jdx.dev/checks#check-permissions)
* [jactionlint - invalid-permissions](https://jactionlint.jdx.dev/rules#invalid-permissions)
