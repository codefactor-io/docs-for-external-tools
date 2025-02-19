Pattern: Positive tabindex value

Issue: -

## Description

Using positive tabindex values disrupts the natural tab order of the page and makes navigation difficult for keyboard users. Only use tabindex="0" to make elements focusable or tabindex="-1" to remove elements from navigation.

## Examples

Example of **incorrect** code:
```jsx
<div tabIndex="1">First</div>
<button tabIndex="2">Second</button>
<span tabIndex="5">Jump ahead</span>
```

Example of **correct** code:
```jsx
<div tabIndex="0">Focusable</div>
<button>Naturally focusable</button>
<span tabIndex="-1">Not in tab order</span>
```