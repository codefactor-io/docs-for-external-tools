Pattern: Invalid string in `typeof` comparison

Issue: -

## Description

The `typeof` operator can only return one of: "undefined", "object", "boolean", "number", "string", "function", "symbol", or "bigint". Comparing typeof against any other string is likely a typing mistake and will always evaluate to false.

## Examples

Example of **incorrect** code:
```javascript
typeof foo === "strnig"
typeof foo == "undefimed"
typeof bar != "nunber"
typeof baz !== "function"

// Comparing to a variable
typeof foo === someVariable;
```

Example of **correct** code:
```javascript
typeof foo === "string"
typeof foo == "undefined"
typeof bar != "number"
typeof baz !== "function"
typeof qux === "object"
typeof sym === "symbol"
typeof value === "bigint"
```