Pattern: Same function call in consecutive `if`s

Issue: -

## Description

This is probably a copy & paste error.
Despite the fact that function can have side effects and `if` works as
intended, such an approach is implicit and can be considered a "code smell".

## What it does

Checks for consecutive `if`s with the same function call.

## Examples

```rust
if foo() == bar {
    …
} else if foo() == bar {
    …
}
```

This probably should be:
```rust
if foo() == bar {
    …
} else if foo() == baz {
    …
}
```

or if the original code was not a typo and called function mutates a state,
consider move the mutation out of the `if` condition to avoid similarity to
a copy & paste error:

```rust
let first = foo();
if first == bar {
    …
} else {
    let second = foo();
    if second == bar {
    …
    }
}
```

## Further Reading

* [Clippy - same_functions_in_if_condition](https://clippy.rust-lang.org/stable/index.html#same_functions_in_if_condition)
