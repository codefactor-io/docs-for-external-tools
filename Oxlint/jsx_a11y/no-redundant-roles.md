Pattern: Redundant ARIA role

Issue: -

## Description

Elements should not be given explicit ARIA roles that match their implicit roles. These redundant roles add unnecessary verbosity to the accessibility tree.

## Examples

Example of **incorrect** code:
```jsx
<nav role="navigation" />
<button role="button" />
<img role="img" alt="Logo" />
```

Example of **correct** code:
```jsx
<nav />
<button />
<img alt="Logo" />
<div role="button" />
```