Pattern: Use of labeled statement

Issue: -

## Description

Labeled statements are a rarely used flow control feature that can make code harder to understand and maintain. While they can be useful for breaking out of nested loops, there are often clearer alternatives like extracting loops into functions or using other control flow structures.

## Examples

Example of **incorrect** code:
```javascript
outer: while(true) {
  inner: while(true) {
    break outer;
  }
}

label: {
  break label;
}

loop1: for(let i = 0; i < 5; i++) {
  continue loop1;
}
```

Example of **correct** code:
```javascript
function processLoop() {
  while(true) {
    if (condition) return;
  }
}

while(true) {
  if (condition) break;
}

for(let i = 0; i < 5; i++) {
  if (condition) continue;
}
```