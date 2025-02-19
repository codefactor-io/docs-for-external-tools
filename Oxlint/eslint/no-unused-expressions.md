Pattern: Expression statement without effect

Issue: -

## Description

Expressions that don't affect program state are likely mistakes. These include standalone type expressions, type assertions, non-null assertions, and other expressions that aren't used in assignments, function calls, or other meaningful operations.

## Examples

Example of **incorrect** code:
```javascript
'use strict';  // not in directive position
a + b;
new Set<number>;
obj?.prop;
condition ? 'a' : 'b';
void 0;
x == y;

// TypeScript
type;
foo as string;
value!;
```

Example of **correct** code:
```javascript
const result = a + b;
const set = new Set<number>();
const value = obj?.prop;
const str = condition ? 'a' : 'b';
const comparison = x == y;

// Side effects are ok
alert('hi');
[1, 2, 3].forEach(n => console.log(n));

// Assignment expressions
x = 0;
x += 1;
x++;
```