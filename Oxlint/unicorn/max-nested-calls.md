Pattern: Nested calls exceeding maximum depth

Issue: -

## Description

Deeply nested calls make code hard to read. Extracting intermediate
results into named variables improves readability.

## Examples

Example of **incorrect** code:
```javascript
foo(bar(baz(qux())));
```

Example of **correct** code:
```javascript
const value = baz(qux());
foo(bar(value));

// Fluent chains are ignored.
query().filter().map().toArray();
```
