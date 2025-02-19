Pattern: Inline function in `removeEventListener`

Issue: -

## Description

Using an inline function or the result of an inline `.bind()` call in `removeEventListener` won't remove the original listener. You must use the same function reference that was passed to `addEventListener`.

## Examples

Example of **incorrect** code:
```javascript
el.removeEventListener("click", () => {});
el.removeEventListener("click", function () {});
```

Example of **correct** code:
```javascript
el.removeEventListener("click", handler);
el.removeEventListener("click", handler.bind(this));
```