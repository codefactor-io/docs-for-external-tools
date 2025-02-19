Pattern: Unsupported ARIA property

Issue: -

## Description

Elements with ARIA roles can only use ARIA attributes that are supported by that role. Using unsupported ARIA attributes on elements has no effect and may confuse assistive technologies.

## Examples

Example of **incorrect** code:
```jsx
<button role="checkbox" aria-level="2" />
<div role="heading" aria-checked="true" />
<span role="progressbar" aria-selected="true" />
```

Example of **correct** code:
```jsx
<button role="checkbox" aria-checked="false" />
<div role="heading" aria-level="2" />
<span role="progressbar" aria-valuenow="50" />
```