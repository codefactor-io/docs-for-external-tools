Pattern: DOM node insertion via `appendChild`

Issue: -

## Description

The `append()` method is more versatile than `appendChild()` as it can handle multiple nodes and both DOM nodes and strings in a single call.

## Examples

Example of **incorrect** code:
```javascript
foo.appendChild(bar);
```

Example of **correct** code:
```javascript
foo.append(bar);
foo.append(textNode, elementNode, "text");
```