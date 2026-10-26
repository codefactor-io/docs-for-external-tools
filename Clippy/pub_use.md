Pattern: Use of `pub use`

Issue: -

## Description

A project may wish to limit `pub use` instances to prevent
unintentional exports, or to encourage placing exported items directly in public modules.

## What it does

Restricts the usage of `pub use ...`

## Examples

Example of **incorrect** code:

```rust
pub mod outer {
    mod inner {
        pub struct Test {}
    }
    pub use inner::Test;
}

use outer::Test;
```

Example of **correct** code:

```rust
pub mod outer {
    pub struct Test {}
}

use outer::Test;
```

## Further Reading

* [Clippy - pub_use](https://clippy.rust-lang.org/stable/index.html#pub_use)
