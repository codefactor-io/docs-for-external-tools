Pattern: Use of disallowed field

Issue: -

## Description

Some fields are undesirable in certain contexts, and it's beneficial to
lint for them as needed.

## What it does

Denies the configured fields in clippy.toml

Note: Even though this lint is warn-by-default, it will only trigger if
fields are defined in the clippy.toml file.

## Examples

An example clippy.toml configuration:
```toml
# clippy.toml
disallowed-fields = [
    # Can use a string as the path of the disallowed field.
    "std::ops::Range::start",
    # Can also use an inline table with a `path` key.
    { path = "std::ops::Range::start" },
    # When using an inline table, can add a `reason` for why the field
    # is disallowed.
    { path = "std::ops::Range::start", reason = "The start of the range is not used" },
]
```

```rust
use std::ops::Range;

let range = Range { start: 0, end: 1 };
println!("{}", range.start); // `start` is disallowed in the config.
```

Use instead:
```rust
use std::ops::Range;

let range = Range { start: 0, end: 1 };
println!("{}", range.end); // `end` is _not_ disallowed in the config.
```

## Further Reading

* [Clippy - disallowed_fields](https://clippy.rust-lang.org/stable/index.html#disallowed_fields)
