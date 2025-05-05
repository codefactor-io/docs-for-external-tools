Pattern: Disallowed C++17 feature

Issue: -

## Description

`<filesystem>` header does not have sufficient support for testing, and suffers from inherent security vulnerabilities.

`<filesystem>` wraps system calls like `rename` rather than `renameat` and so doesn’t allow resolving a filename without being subject to symlink attacks. This doesn’t affect all use cases.


## Further Reading

* [Google C++ Style Guide - Disallowed standard library features](https://google.github.io/styleguide/cppguide.html#Disallowed_Stdlib)