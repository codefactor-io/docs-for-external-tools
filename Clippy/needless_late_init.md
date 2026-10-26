Pattern: Unnecessary late initialization

Issue: -

## Description

Assigning in the `let` statement is less repetitive.

## What it does

Checks for late initializations that can be replaced by a `let` statement
with an initializer.

## Examples

Example of **incorrect** code:

```rust
let a;
a = 1;

let b;
match 3 {
    0 => b = "zero",
    1 => b = "one",
    _ => b = "many",
}

let c;
if true {
    c = 1;
} else {
    c = -1;
}
```

Example of **correct** code:

```rust
let a = 1;

let b = match 3 {
    0 => "zero",
    1 => "one",
    _ => "many",
};

let c = if true {
    1
} else {
    -1
};
```

## Further Reading

* [Clippy - needless_late_init](https://clippy.rust-lang.org/stable/index.html#needless_late_init)
