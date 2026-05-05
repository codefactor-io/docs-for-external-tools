Pattern: Malformed package name

Issue: -

## Description

Checks that package names follow Go conventions and best practices. It helps prevent using bad package names and enforces consistent naming patterns. This rule arose from package naming checks in `var-naming.

By default, it checks for:

    Package name conventions (no underscores except for test packages, no MixedCaps).
    Bad package names from the official Go blog (e.g., `common`, `util`, `utils`, `misc`, `interfaces`, `types`).
    Package names that conflict with common Go standard library packages (e.g., `http`, `json`, `fmt`).


## Further Reading

* [Revive - package-naming](https://revive.run/r#package-naming)