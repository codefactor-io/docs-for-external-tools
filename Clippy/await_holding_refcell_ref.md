Pattern: `RefCell` reference held across `await`

Issue: -

## Description

`RefCell` refs only check for exclusive mutable access
at runtime. Holding a `RefCell` ref across an await suspension point
risks panics from a mutable ref shared while other refs are outstanding.

## What it does

Checks for calls to `await` while holding a `RefCell`, `Ref`, or `RefMut`.

## Examples

Example of **incorrect** code:

```rust
async fn foo(x: &RefCell<u32>) {
  let mut y = x.borrow_mut();
  *y += 1;
  baz().await;
}

async fn bar(x: &RefCell<u32>) {
  let mut y = x.borrow_mut();
  *y += 1;
  drop(y); // explicit drop
  baz().await;
}
```

Example of **correct** code:

```rust
async fn foo(x: &RefCell<u32>) {
  {
     let mut y = x.borrow_mut();
     *y += 1;
  }
  baz().await;
}

async fn bar(x: &RefCell<u32>) {
  {
    let mut y = x.borrow_mut();
    *y += 1;
  } // y dropped here at end of scope
  baz().await;
}
```

## Known problems

Will report false positive for explicitly dropped refs
([#6353](https://github.com/rust-lang/rust-clippy/issues/6353)). A workaround for this is
to wrap the `.borrow[_mut]()` call in a block instead of explicitly dropping the ref.

## Further Reading

* [Clippy - await_holding_refcell_ref](https://clippy.rust-lang.org/stable/index.html#await_holding_refcell_ref)
