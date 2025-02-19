Pattern: Invalid ARIA role

Issue: -

## Description

Elements with ARIA roles must use valid, non-abstract roles from the WAI-ARIA specification. Invalid or abstract roles will not be properly interpreted by assistive technologies.

## Examples

Example of **incorrect** code:
```jsx
<div role="datepicker" />
<span role="range" />
<button role="" />
<div role="invalid-role" />
```

Example of **correct** code:
```jsx
<div role="button" />
<span role="alert" />
<div role="tabpanel" />
<div role={dynamicRole} />
```