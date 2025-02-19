Pattern: Missing required ARIA attribute

Issue: -

## Description

Elements with ARIA roles must have all required ARIA attributes for that role. Missing required attributes prevents assistive technologies from correctly interpreting the element's purpose and state.

## Examples

Example of **incorrect** code:
```jsx
<div role="checkbox" />
<span role="spinbutton" />
<div role="slider" />
```

Example of **correct** code:
```jsx
<div role="checkbox" aria-checked="false" />
<span role="spinbutton" aria-valuenow="50" aria-valuemin="0" aria-valuemax="100" />
<div role="slider" aria-valuenow="5" aria-valuemin="0" aria-valuemax="10" />
```