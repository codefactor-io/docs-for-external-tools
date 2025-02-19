Pattern: Invalid autocomplete value

Issue: -

## Description

The autocomplete attribute on form inputs must use valid values from the HTML specification. Invalid values can decrease accessibility and prevent browsers from properly assisting users with form completion.

## Examples

Example of **incorrect** code:
```jsx
<input autocomplete="user-name" />
<input autocomplete="random" />
<input autocomplete="email-address" />
```

Example of **correct** code:
```jsx
<input autocomplete="name" />
<input autocomplete="email" />
<input autocomplete="street-address" />
```