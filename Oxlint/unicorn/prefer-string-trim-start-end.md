Pattern: Directional trim method names

Issue: -

## Description

The `trimLeft` and `trimRight` methods are legacy aliases that can be confusing due to their direction-dependent naming. Use `trimStart` and `trimEnd` instead for better consistency with other language features and clearer directional independence.

## Examples

Example of **incorrect** code:
```javascript
str.trimLeft();
str.trimRight();
```

Example of **correct** code:
```javascript
str.trimStart();
str.trimEnd();
```