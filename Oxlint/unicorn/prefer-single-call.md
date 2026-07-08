Pattern: Multiple consecutive calls to the same variadic method

Issue: -

## Description

Calling the same variadic method on the same receiver multiple times
consecutively can be merged into a single call, which is more concise
and can be marginally more performant.

## Examples

Example of **incorrect** code:
```javascript
foo.push(1);
foo.push(2);

foo.unshift(1);
foo.unshift(2);

element.classList.add("foo");
element.classList.add("bar");

importScripts("foo.js");
importScripts("bar.js");
```

Example of **correct** code:
```javascript
foo.push(1, 2);

foo.unshift(2, 1);

element.classList.add("foo", "bar");

importScripts("foo.js", "bar.js");
```
