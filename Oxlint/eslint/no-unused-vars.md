Pattern: Variable declaration without usage

Issue: -

## Description

Variables, functions, or type declarations that are never used indicate dead code or incomplete refactoring. A variable is considered used when it's read, called, constructed, passed as an argument, or exported. Just declaring or assigning to a variable doesn't count as usage.

## Examples

Example of **incorrect** code:
```javascript
var x;
let y = 5;
const z = 'unused';

function unused(a, b) {  // b is never used
  return a;
}

class UnusedClass {}

// TypeScript
type UnusedType = string;
interface UnusedInterface {}
enum UnusedEnum { A, B }

// Write-only variables
let counter = 0;
counter = counter + 1;  // Only modified, never read
```

Example of **correct** code:
```javascript
var x = 5;
console.log(x);

function used(a, b) {
  return a + b;
}
used(1, 2);

export class UsedClass {}

// TypeScript
type UsedType = string;
const name: UsedType = 'test';

interface Props {
  x: number;
}
function createElement(props: Props) {}

// Reading after write is usage
let counter = 0;
counter++;
return counter;
```