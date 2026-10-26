Pattern: Unnecessary `continue`

Issue: -

## Description

Having explicit `else` blocks for `if` statements
containing `continue` in their THEN branch adds unnecessary branching and
nesting to the code. Having an else block containing just `continue` can
also be better written by grouping the statements following the whole `if`
statement within the THEN block and omitting the else block completely.

## What it does

The lint checks for `if`-statements appearing in loops
that contain a `continue` statement in either their main blocks or their
`else`-blocks, when omitting the `else`-block possibly with some
rearrangement of code can make the code easier to understand.
The lint also checks if the last statement in the loop is a `continue`

## Examples

```rust
while condition() {
    update_condition();
    if x {
        // ...
    } else {
        continue;
    }
    println!("Hello, world");
}
```

Could be rewritten as

```rust
while condition() {
    update_condition();
    if x {
        // ...
        println!("Hello, world");
    }
}
```

As another example, the following code

```rust
loop {
    if waiting() {
        continue;
    } else {
        // Do something useful
    }
}
```
Could be rewritten as

```rust
loop {
    if waiting() {
        continue;
    }
    // Do something useful
}
```

```rust

fn foo() -> ErrorKind { ErrorKind::NotFound }
for _ in 0..10 {
    match foo() {
        ErrorKind::NotFound => {
            eprintln!("not found");
            continue
        }
        ErrorKind::TimedOut => {
            eprintln!("timeout");
            continue
        }
        _ => {
            eprintln!("other error");
            continue
        }
    }
}
```
Could be rewritten as


```rust

fn foo() -> ErrorKind { ErrorKind::NotFound }
for _ in 0..10 {
    match foo() {
        ErrorKind::NotFound => {
            eprintln!("not found");
        }
        ErrorKind::TimedOut => {
            eprintln!("timeout");
        }
        _ => {
            eprintln!("other error");
        }
    }
}
```

## Further Reading

* [Clippy - needless_continue](https://clippy.rust-lang.org/stable/index.html#needless_continue)
