Pattern: Unnecessary `filter_map()`

Issue: -

## Description

Complexity. The intent is also clearer if only a single
operation is being performed.

## What it does

Checks for `filter_map` calls that could be replaced by `filter` or `map`.
More specifically it checks if the closure provided is only performing one of the
filter or map operations and suggests the appropriate option.

## Examples

```rust
let _ = (0..3).filter_map(|x| if x > 2 { Some(x) } else { None });

// As there is no transformation of the argument this could be written as:
let _ = (0..3).filter(|&x| x > 2);
```

```rust
let _ = (0..4).filter_map(|x| Some(x + 1));

// As there is no conditional check on the argument this could be written as:
let _ = (0..4).map(|x| x + 1);
```

## Further Reading

* [Clippy - unnecessary_filter_map](https://clippy.rust-lang.org/stable/index.html#unnecessary_filter_map)
