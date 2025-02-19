Pattern: Invalid ARIA attribute

Issue: -

## Description

Only use valid ARIA attributes as defined in the WAI-ARIA specification. Invalid or misspelled ARIA attributes will be ignored by assistive technologies, reducing accessibility.

## Examples

Example of **incorrect** code:
```jsx
<div aria-labeledby="id" />
<button aria-describedby="id" aria-pressed="yes" />
<input aria-invalid="true" aria-required="yes" />
```

Example of **correct** code:
```jsx
<div aria-labelledby="id" />
<button aria-describedby="id" aria-pressed="true" />
<input aria-invalid="true" aria-required="true" />
```