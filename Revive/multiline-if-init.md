Pattern: Multiline `if` init clause

Issue: -

## Description

Flags `if` statements whose init clause spans multiple lines. The if-init idiom exists for tight one-liners. When the init wraps across lines, the reader has to visually parse a struct literal or call chain to find where the initialization ends and the condition begins. Extract the initialization to a separate statement instead.

## Examples

Example of **incorrect** code:

```go
if r, err := rec(
	ctx,
	mgr.GetClient(),
	mgr.GetFieldIndexer(),
	mgr.GetEventRecorderFor(fmt.Sprintf("%s-%s-controller", name, options.ManagerName)),
	opts...,
); err != nil {
	return err
}
```

Example of **correct** code:

```go
r, err := rec(
	ctx,
	mgr.GetClient(),
	mgr.GetFieldIndexer(),
	mgr.GetEventRecorderFor(fmt.Sprintf("%s-%s-controller", name, options.ManagerName)),
	opts...,
)
if err != nil {
	return err
}
```

## Further Reading

* [Revive - multiline-if-init](https://revive.run/r#multiline-if-init)
