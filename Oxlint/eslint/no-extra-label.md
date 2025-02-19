Pattern: Unnecessary labeled break/continue

Issue: -

## Description

Labels on loops are only needed when breaking/continuing to that label from a nested loop or switch. If there are no nested loops or switches, the label is unnecessary and can be confusing as developers expect labels to handle more complex flow control.

## Examples

Example of **incorrect** code:
```javascript
outer: while (condition) {
  break outer;
}

loop1: for (let i = 0; i < 3; i++) {
  continue loop1;
}

check: switch (value) {
  case 1:
    break check;
}
```

Example of **correct** code:
```javascript
while (condition) {
  break;
}

outer: while (condition1) {
  while (condition2) {
    break outer;
  }
}

loop1: for (let i = 0; i < 3; i++) {
  for (let j = 0; j < 3; j++) {
    continue loop1;
  }
}
```