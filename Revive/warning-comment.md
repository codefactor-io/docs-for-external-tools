Pattern: Unresolved warning comment

Issue: -

## Description

Developers often add comments to code which is not complete or needs review. Most likely you want to fix or review the code, and then remove the comment, before you consider the code to be production ready.

## Examples

Example of **incorrect** code:

```go
// FIXME: this is not a good idea
// TODO: need code review
experiment()
```

Example of **correct** code:

```go
// NOT READY FOR PRIME TIME
// but too bad, it is not a predefined warning term
experiment()
```
