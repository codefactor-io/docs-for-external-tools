Pattern: Inconsistent use of `{}`

Issue: -

## Description

Omitting curly braces can reduce code readability and increase the likelihood of errors, especially in deeply nested or indented code. It can also lead to bugs if additional statements are added later without properly enclosing them in braces. Using curly braces consistently makes the code safer and easier to modify.

## Examples

Example of **incorrect** code:

```javascript
/* curly: ["error", "all"] */

if (foo) foo++;
while (bar) bar--;
do foo();
while (bar);
```

Example of **correct** code:

```javascript
/* curly: ["error", "all"] */

if (foo) {
  foo++;
}
while (bar) {
  bar--;
}
do {
  foo();
} while (bar);
```