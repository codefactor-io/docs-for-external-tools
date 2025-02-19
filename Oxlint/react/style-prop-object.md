Pattern: Non-object value in `style` prop

Issue: -

## Description

The `style` prop in React components must receive an object that maps style properties to their values. Using strings, booleans, or other non-object values will not work as expected.

## Examples

Example of **incorrect** code:
```jsx
<div style="color: 'red'" />
<div style={true} />
<Hello style={true} />
const styles = true;
<div style={styles} />
```

Example of **correct** code:
```jsx
<div style={{ color: "red" }} />
<Hello style={{ color: "red" }} />
const styles = { color: "red" };
<div style={styles} />
```