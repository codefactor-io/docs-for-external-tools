Pattern: Template literal placeholder in string literal

Issue: -

## Description

Using template literal placeholder syntax (`${expression}`) in regular string literals results in a literal string containing the placeholder rather than the evaluated expression. This is usually a mistake where backticks were intended instead of quotes.

## Examples

Example of **incorrect** code:
```javascript
const name = "John";
const greeting = "Hello ${name}";  // Results in "Hello ${name}"

const time = "Time: ${12 * 60 * 60 * 1000}";

const message = 'Welcome ${user.name}!';

const error = "Error: ${err.message}";
```

Example of **correct** code:
```javascript
const name = "John";
const greeting = `Hello ${name}`;  // Results in "Hello John"

const time = `Time: ${12 * 60 * 60 * 1000}`;

const message = `Welcome ${user.name}!`;

const error = `Error: ${err.message}`;
```