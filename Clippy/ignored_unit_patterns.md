Pattern: Use of `_` pattern for unit value

Issue: -

## Description

Matching with `()` explicitly instead of `_` outlines
the fact that the pattern contains no data. Also it
would detect a type change that `_` would ignore.

## What it does

Checks for usage of `_` in patterns of type `()`.

## Examples

Example of **incorrect** code:

```rust
match std::fs::create_dir("tmp-work-dir") {
    Ok(_) => println!("Working directory created"),
    Err(s) => eprintln!("Could not create directory: {s}"),
}
```

Example of **correct** code:

```rust
match std::fs::create_dir("tmp-work-dir") {
    Ok(()) => println!("Working directory created"),
    Err(s) => eprintln!("Could not create directory: {s}"),
}
```

## Further Reading

* [Clippy - ignored_unit_patterns](https://clippy.rust-lang.org/stable/index.html#ignored_unit_patterns)
