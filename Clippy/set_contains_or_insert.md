Pattern: Set `contains()` followed by `insert()`

Issue: -

## Description

Using just `insert` and checking the returned `bool` is more efficient.

## What it does

Checks for usage of `contains` to see if a value is not present
in a set like `HashSet` or `BTreeSet`, followed by an `insert`.

## Examples

Example of **incorrect** code:

```rust
use std::collections::HashSet;
let mut set = HashSet::new();
let value = 5;
if !set.contains(&value) {
    set.insert(value);
    println!("inserted {value:?}");
}
```

Example of **correct** code:

```rust
use std::collections::HashSet;
let mut set = HashSet::new();
let value = 5;
if set.insert(&value) {
    println!("inserted {value:?}");
}
```

## Known problems

In case the value that wants to be inserted is borrowed and also expensive or impossible
to clone. In such a scenario, the developer might want to check with `contains` before inserting,
to avoid the clone. In this case, it will report a false positive.

## Further Reading

* [Clippy - set_contains_or_insert](https://clippy.rust-lang.org/stable/index.html#set_contains_or_insert)
