Pattern: Redundant boolean type cast

Issue: -

## Description

In contexts where expression results are automatically coerced to boolean (like `if` conditions), using explicit boolean casts (`!!` or `Boolean()`) is unnecessary. These extra casts make code harder to read without adding any functional benefit.

## Examples

Example of **incorrect** code:
```javascript
if (!!foo) {
  // ...
}

while (!!bar) {
  // ...
}

const baz = !!!qux;

if (Boolean(foo)) {
  // ...
}

const valid = !!(a && b);
```

Example of **correct** code:
```javascript
if (foo) {
  // ...
}

while (bar) {
  // ...
}

const baz = !qux;

// When explicitly converting to boolean outside of boolean contexts
const bool = Boolean(foo);

const valid = a && b;
```