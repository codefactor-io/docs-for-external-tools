Pattern: Unnecessary `find_map()`

Issue: -

## Description

Complexity. The intent is also clearer if only a single
operation is being performed.

## What it does

Checks for `find_map` calls that could be replaced by `find` or `map`. More
specifically it checks if the closure provided is only performing one of the
find or map operations and suggests the appropriate option.

## Examples

```rust
let _ = (0..3).find_map(|x| if x > 2 { Some(x) } else { None });

// As there is no transformation of the argument this could be written as:
let _ = (0..3).find(|&x| x > 2);
```

```rust
let _ = (0..4).find_map(|x| Some(x + 1));

// As there is no conditional check on the argument this could be written as:
let _ = (0..4).map(|x| x + 1).next();
```

## Further Reading

* [Clippy - unnecessary_find_map](https://clippy.rust-lang.org/stable/index.html#unnecessary_find_map)
