Pattern: Package directory name mismatch

Issue: -

## Description

It is considered a good practice to name a package after the directory containing it. This rule warns when the package name declared in the file does not match the name of the directory containing the file.

The following cases are excluded from this check:

    Package `main` (executable packages)
    Files in `testdata` directories (at any level) - by default
    Files directly in `internal` directories (but files in subdirectories of internal are checked)

For test files (files with `_test` suffix), package name additionally checked if it matches directory name with `_test` suffix appended.


## Further Reading

* [Revive - package-directory-mismatch](https://revive.run/r#package-directory-mismatch)