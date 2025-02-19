Pattern: Negated condition in control flow

Issue: -

## Description

Using negated conditions makes code harder to understand. Improve readability by inverting the condition and swapping the consequent and alternate branches.

## Examples

Example of **incorrect** code:
```javascript
if (!a) {
  doSomethingC();
} else {
  doSomethingB();
}

!a ? doSomethingC() : doSomethingB();
```

Example of **correct** code:
```javascript
if (a) {
  doSomethingB();
} else {
  doSomethingC();
}

a ? doSomethingB() : doSomethingC();
```