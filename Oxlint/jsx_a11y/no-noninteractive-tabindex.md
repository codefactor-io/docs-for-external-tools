Pattern: Tabindex on non-interactive element

Issue: -

## Description

Non-interactive elements should not have tabindex values that make them focusable. Screen readers already provide mechanisms to navigate through page content, and adding unnecessary tab stops increases cognitive load.

## Examples

Example of **incorrect** code:
```jsx
<div tabIndex="0" />
<article tabIndex="0" />
<span tabIndex={0} />
<p tabIndex="0">Text</p>
```

Example of **correct** code:
```jsx
<button tabIndex="0" />
<div role="button" tabIndex="0" />
<input tabIndex="0" />
<div tabIndex="-1" />
```