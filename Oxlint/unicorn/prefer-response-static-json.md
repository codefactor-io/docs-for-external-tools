Pattern: JSON response created with `JSON.stringify`

Issue: -

## Description

`Response.json()` is a more concise and semantically clear way to create JSON responses.
It automatically sets the correct `Content-Type` header (`application/json`) and handles
serialization, making the code more maintainable and less error-prone.

## Examples

Example of **incorrect** code:
```javascript
const response = new Response(JSON.stringify(data));
const response = new Response(JSON.stringify(data), { status: 200 });
```

Example of **correct** code:
```javascript
const response = Response.json(data);
const response = Response.json(data, { status: 200 });
```
