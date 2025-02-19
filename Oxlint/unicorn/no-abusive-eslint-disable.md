Pattern: Unspecified rules in `eslint-disable` comment

Issue: -

## Description

Using `eslint-disable` comments without specifying which rules to disable can lead to silently ignoring important errors. Always explicitly list the rules that need to be disabled.

## Examples

Example of **incorrect** code:
```javascript
/* eslint-disable */
console.log(message);

console.log(message); // eslint-disable-line

// eslint-disable-next-line
console.log(message);
```

Example of **correct** code:
```javascript
/* eslint-disable no-console */
console.log(message);

console.log(message); // eslint-disable-line no-console

// eslint-disable-next-line no-console
console.log(message);
```