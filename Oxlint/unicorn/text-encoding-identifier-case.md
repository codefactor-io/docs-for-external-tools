Pattern: Inconsistent text encoding identifier case

Issue: -

## Description

Text encoding identifiers should use consistent lowercase format (`utf8`, `ascii`) for better readability and convention adherence. The ECMAScript specification doesn't define case sensitivity for these identifiers, but lowercase is the common practice.

## Examples

Example of **incorrect** code:
```javascript
await fs.readFile(file, "UTF-8");
await fs.readFile(file, "ASCII");
const string = buffer.toString("utf-8");
```

Example of **correct** code:
```javascript
await fs.readFile(file, "utf8");
await fs.readFile(file, "ascii");
const string = buffer.toString("utf8");
```