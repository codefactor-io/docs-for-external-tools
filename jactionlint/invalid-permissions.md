Pattern: Invalid permission

Issue: -

## Description

A `permissions` setting uses an unknown scope or an unsupported access level. Use `read`, `write`, or `none` for scopes that support them, or `read-all`, `write-all`, or `{}` for the entire setting.

## Examples

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
