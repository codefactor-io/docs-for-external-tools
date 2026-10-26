Pattern: `self` only used in recursion

Issue: -

## Description

It may be possible to remove the `self` argument, allowing the function to be
used without an object of type `Self`.

## What it does

Checks for `self` receiver that is only used in recursion with no side-effects.

## Examples

Example of **incorrect** code:

```rust
struct Foo;
impl Foo {
    fn f(&self, n: u32) -> u32 {
        if n == 0 {
            1
        } else {
            n * self.f(n - 1)
        }
    }
}
```

Example of **correct** code:

```rust
struct Foo;
impl Foo {
    fn f(n: u32) -> u32 {
        if n == 0 {
            1
        } else {
            n * Self::f(n - 1)
        }
    }
}
```

## Known problems

Too many code paths in the linting code are currently untested and prone to produce false
positives or are prone to have performance implications.

In some cases, this would not catch all useless arguments.

```rust
struct Foo;
impl Foo {
    fn foo(&self, a: usize) -> usize {
        let f = |x| x;

        if a == 0 {
            1
        } else {
            f(self).foo(a)
        }
    }
}
```

For example, here `self` is only used in recursion, but the lint would not catch it.

List of some examples that can not be caught:
- binary operation of non-primitive types
- closure usage
- some `break` relative operations
- struct pattern binding

Also, when you recurse the function name with path segments, it is not possible to detect.

## Further Reading

* [Clippy - self_only_used_in_recursion](https://clippy.rust-lang.org/stable/index.html#self_only_used_in_recursion)
