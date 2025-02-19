Pattern: Side effect in module initialization

Issue: -

## Description

Side effects during module initialization can prevent effective tree-shaking by bundlers. When modules have side effects, bundlers cannot safely eliminate unused code, resulting in larger bundles. Module initialization should be kept pure to allow optimal code elimination.

## Examples

Example of **incorrect** code:
```javascript
myGlobal = 17; // Cannot determine side-effects of assignment to global variable
const x = { [globalFunction()]: "myString" }; // Cannot determine side-effects of calling global function
```

Example of **correct** code:
```javascript
const localVar = 17; // Local variable assignment, no global side-effects
export default 42; // Pure export with no side-effects
```