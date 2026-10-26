Pattern: Item declared after statement

Issue: -

## Description

Items live for the entire scope they are declared
in. But statements are processed in order. This might cause confusion as
it's hard to figure out which item is meant in a statement.

## What it does

Checks for items declared after some statement in a block.

## Examples

Example of **incorrect** code:

```rust
fn foo() {
    println!("cake");
}

fn main() {
    foo(); // prints "foo"
    fn foo() {
        println!("foo");
    }
    foo(); // prints "foo"
}
```

Example of **correct** code:

```rust
fn foo() {
    println!("cake");
}

fn main() {
    fn foo() {
        println!("foo");
    }
    foo(); // prints "foo"
    foo(); // prints "foo"
}
```

## Further Reading

* [Clippy - items_after_statements](https://clippy.rust-lang.org/stable/index.html#items_after_statements)
