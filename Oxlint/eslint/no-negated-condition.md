Pattern: Negated condition in if statement or ternary

Issue: -

## Description

Using negated conditions with else clauses makes code harder to read. The code can be made more readable by inverting the condition and swapping the if/else blocks or ternary expressions.

## Examples

Example of **incorrect** code:
```javascript
if (!condition) {
  doSomething();
} else {
  doSomethingElse();
}

!condition ? doSomething() : doSomethingElse();

if (!a && !b) {
  doSomething();
} else {
  doOtherThing();
}
```

Example of **correct** code:
```javascript
if (condition) {
  doSomethingElse();
} else {
  doSomething();
}

condition ? doSomethingElse() : doSomething();

// When there's no else clause, negation is fine
if (!condition) {
  doSomething();
}
```