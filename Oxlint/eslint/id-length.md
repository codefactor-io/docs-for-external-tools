Pattern: Improper identifier length

Issue: -

## Description

Very short identifier names (like `e`, `x`, `_t`) or very long ones can make code harder to read and maintain. This rule enforces minimum and/or maximum identifier length conventions to improve code clarity and readability.

## Examples

Example of **incorrect** code:
```javascript
// With default minimum length of 2
const x = 5;
obj.e = document.body;
const foo = function(e) {};
try {
  dangerousStuff();
} catch (e) {
  // ignore as many do
}
const myObj = { a: 1 };
((a) => {
  a * a;
});
class y {}
```

Example of **correct** code:
```javascript
// With default minimum length of 2
const num = 5;
obj.el = document.body;
const foo = function(evt) {/* do stuff */};
try {
  dangerousStuff();
} catch (error) {
  // ignore as many do
}
const myObj = { apple: 1 };
((num) => {
  num * num;
});
class MyClass {}
```