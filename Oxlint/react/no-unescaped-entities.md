Pattern: Unescaped entity in JSX text

Issue: -

## Description

Special characters in JSX text nodes need to be properly escaped to prevent syntax errors and ensure correct rendering. Use HTML entities or JSX expressions for special characters.

## Examples

Example of **incorrect** code:
```jsx
<div> > </div>
```

Example of **correct** code:
```jsx
<div> &gt; </div>
<div> {">"} </div>
```