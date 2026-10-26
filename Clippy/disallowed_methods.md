Pattern: Use of disallowed method

Issue: -

## Description

Some methods are undesirable in certain contexts, and it's beneficial to
lint for them as needed.

## What it does

Denies the configured methods and functions in clippy.toml

Note: Even though this lint is warn-by-default, it will only trigger if
methods are defined in the clippy.toml file.

## Examples

An example clippy.toml configuration:
```toml
# clippy.toml
disallowed-methods = [
    # Can use a string as the path of the disallowed method.
    "std::boxed::Box::new",
    # Can also use an inline table with a `path` key.
    { path = "std::time::Instant::now" },
    # When using an inline table, can add a `reason` for why the method
    # is disallowed.
    { path = "std::vec::Vec::leak", reason = "no leaking memory" },
    # Can also add a `replacement` that will be offered as a suggestion.
    { path = "std::sync::Mutex::new", reason = "prefer faster & simpler non-poisonable mutex", replacement = "parking_lot::Mutex::new" },
    # This would normally error if the path is incorrect, but with `allow-invalid` = `true`,
    # it will be silently ignored
    { path = "std::fs::InvalidPath", reason = "use alternative instead", allow-invalid = true },
]
```

```rust
let xs = vec![1, 2, 3, 4];
xs.leak(); // Vec::leak is disallowed in the config.
// The diagnostic contains the message "no leaking memory".

let _now = Instant::now(); // Instant::now is disallowed in the config.

let _box = Box::new(3); // Box::new is disallowed in the config.
```

Use instead:
```rust
let mut xs = Vec::new(); // Vec::new is _not_ disallowed in the config.
xs.push(123); // Vec::push is _not_ disallowed in the config.
```

## Further Reading

* [Clippy - disallowed_methods](https://clippy.rust-lang.org/stable/index.html#disallowed_methods)
