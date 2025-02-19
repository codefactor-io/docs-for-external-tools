Pattern: Member access from `await` expression

Issue: -

## Description

Accessing members directly from an `await` expression requires parentheses, which reduces code readability. Use destructuring or intermediate variables instead.

## Examples

Example of **incorrect** code:
```javascript
async function bad() {
  const secondElement = (await getArray())[1];
}
```

Example of **correct** code:
```javascript
async function good() {
  const [, secondElement] = await getArray();
}
```