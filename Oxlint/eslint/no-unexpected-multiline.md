Pattern: Confusing line break in expression

Issue: -

## Description

Some line breaks in JavaScript can lead to unexpected parsing due to automatic semicolon insertion (ASI). This commonly occurs with function calls, property access, template literals, and division operators when placed on new lines without proper semicolons.

## Examples

Example of **incorrect** code:
```javascript
var a = b
(x || y).doSomething()

var obj = arr
[1, 2, 3].forEach(fn)

let x = function() {}
`hello`

var re = /hello/
/world/.test(str)
```

Example of **correct** code:
```javascript
var a = b;
(x || y).doSomething();

var obj = arr;
[1, 2, 3].forEach(fn);

let x = function() {};
`hello`;

var re = /hello/;
/world/.test(str);

// Or keep on same line
var a = b(x || y).doSomething();
var obj = arr[1, 2, 3].forEach(fn);
```