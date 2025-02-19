Pattern: Use of autofocus

Issue: -

## Description

The autoFocus prop should not be used as it can create usability issues. Autofocusing elements can disorient users, especially those using screen readers, by moving focus unexpectedly.

## Examples

Example of **incorrect** code:
```jsx
<input autoFocus />
<button autoFocus="true" />
<textarea autoFocus={true} />
```

Example of **correct** code:
```jsx
<input />
<button />
<textarea />
```