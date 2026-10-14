Pattern: Inconsistent arrow function body style

Issue: -

## Description

Inconsistent use of block vs. concise bodies makes code harder to read.
Concise bodies are limited to a single expression, whose value is implicitly returned.

## Examples

Example of **incorrect** code:
```javascript
/* arrow-body-style: ["error", "as-needed"] */

/* ✘ Bad: */
const foo = () => {
  return 0;
};
```

Example of **correct** code:
```javascript
/* arrow-body-style: ["error", "as-needed"] */

/* ✔ Good: */
const foo1 = () => 0;

const foo2 = (retv, name) => {
  retv[name] = true;
  return retv;
};

const foo3 = () => {
  bar();
};
```
