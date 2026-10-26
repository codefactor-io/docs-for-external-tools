Pattern: Spawned child process not waited on

Issue: -

## Description

As explained in the [standard library documentation](https://doc.rust-lang.org/stable/std/process/struct.Child.html#warning),
calling `wait()` is necessary on Unix platforms to properly release all OS resources associated with the process.
Not doing so will effectively leak process IDs and/or other limited global resources,
which can eventually lead to resource exhaustion, so it's recommended to call `wait()` in long-running applications.
Such processes are called "zombie processes".

To reduce the rate of false positives, if the spawned process is assigned to a binding, the lint actually works the other way around; it
conservatively checks that all uses of a variable definitely don't call `wait()` and only then emits a warning.
For that reason, a seemingly unrelated use can get called out as calling `wait()` in help messages.

## What it does

Looks for code that spawns a process but never calls `wait()` on the child.

## Examples

Example of **incorrect** code:

```rust
use std::process::Command;

let _child = Command::new("ls").spawn().expect("failed to execute child");
```

Example of **correct** code:

```rust
use std::process::Command;

let mut child = Command::new("ls").spawn().expect("failed to execute child");
child.wait().expect("failed to wait on child");
```

## Control flow

If a `wait()` call exists in an if/then block but not in the else block (or there is no else block),
then this still gets linted as not calling `wait()` in all code paths.
Likewise, when early-returning from the function, `wait()` calls that appear after the return expression
are also not accepted.
In other words, the `wait()` call must be unconditionally reachable after the spawn expression.

## Further Reading

* [Clippy - zombie_processes](https://clippy.rust-lang.org/stable/index.html#zombie_processes)
