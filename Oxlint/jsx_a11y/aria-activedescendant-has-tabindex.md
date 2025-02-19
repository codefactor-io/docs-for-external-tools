Pattern: Missing tabindex with aria-activedescendant

Issue: -

## Description

Elements using aria-activedescendant must be focusable using a tabindex attribute. Without a tabindex, keyboard users cannot navigate to elements controlled by aria-activedescendant.

## Examples

Example of **incorrect** code:
```jsx
<div aria-activedescendant="child-id">
  <div id="child-id">Child</div>
</div>
```

Example of **correct** code:
```jsx
<div aria-activedescendant="child-id" tabIndex={0}>
  <div id="child-id">Child</div>
</div>

<input aria-activedescendant="child-id" />
```