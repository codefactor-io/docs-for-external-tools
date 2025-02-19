Pattern: Concatenation of string literals

Issue: -

## Description

Concatenating string literals together serves no purpose since they could be written as a single string. This pattern often results from incomplete refactoring or string splitting that is no longer necessary.

## Examples

Example of **incorrect** code:
```javascript
var str = "Hello " + "World";
const message = 'a' + `b`;
const template = `foo` + `bar`;

const longString = "this is a " +
                  "long string";

const mixed = "Hello " + `World` + '!';
```

Example of **correct** code:
```javascript
var str = "Hello World";
const message = 'ab';
const template = `foobar`;

const longString = "this is a long string";

// Variables or expressions are fine
const mixed = "Hello " + name + "!";
const dynamic = prefix + "content" + suffix;
```