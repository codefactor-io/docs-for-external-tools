Pattern: Traditional `for` loop for simple iteration

Issue: -

## Description

Using a traditional `for` loop with an index variable for simple array iteration is more verbose and error-prone than using a `for-of` loop, which provides cleaner syntax and eliminates index management.

## Examples

Example of **incorrect** code:
```typescript
for (let i = 0; i < items.length; i++) {
  console.log(items[i]);
}

for (let i = 0; i <= arr.length - 1; i++) {
  doSomething(arr[i]);
}
```

Example of **correct** code:
```typescript
for (const item of items) {
  console.log(item);
}

for (const element of arr) {
  doSomething(element);
}
```