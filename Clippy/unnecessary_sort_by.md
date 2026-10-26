Pattern: Unnecessary `sort_by()`

Issue: -

## Description

It is more clear to use `Vec::sort_by_key` (or `Vec::sort` if
possible) than to use `Vec::sort_by` and a more complicated
closure.

## What it does

Checks for usage of `Vec::sort_by` passing in a closure
which compares the two arguments, either directly or indirectly.

## Examples

Example of **incorrect** code:

```rust
vec.sort_by(|a, b| a.foo().cmp(&b.foo()));
```

Example of **correct** code:

```rust
vec.sort_by_key(|a| a.foo());
```

## Known problems

If the suggested `Vec::sort_by_key` uses Reverse and it isn't already
imported by a use statement, then it will need to be added manually.

## Further Reading

* [Clippy - unnecessary_sort_by](https://clippy.rust-lang.org/stable/index.html#unnecessary_sort_by)
