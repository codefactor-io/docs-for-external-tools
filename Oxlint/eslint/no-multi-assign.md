Pattern: Chained assignment expression

Issue: -

## Description

Chaining assignment expressions can lead to unexpected scope issues and confusion about whether the assignments are meant to be sequential or simultaneous. Separate assignments make the code's intent clearer and prevent accidental global variable creation.

## Examples

Example of **incorrect** code:
```javascript
var a = b = c = 5;

const foo = bar = "baz";

let x = y = z = getValue();

class Example {
  prop = value = 10;
}

a = b = "same value";
```

Example of **correct** code:
```javascript
var a = 5;
var b = 5;
var c = 5;

const foo = "baz";
bar = "baz";

let x = getValue();
let y = getValue();
let z = getValue();

class Example {
  prop = 10;
  value = 10;
}

a = "same value";
b = "same value";
```