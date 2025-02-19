Pattern: Mouse event without keyboard event

Issue: -

## Description

Elements with mouse event handlers (onMouseOver/onMouseOut) must also have corresponding keyboard event handlers (onFocus/onBlur) to ensure keyboard-only users can access the same functionality.

## Examples

Example of **incorrect** code:
```jsx
<div onMouseOver={showTooltip} />
<button onMouseOut={hideMenu} />
```

Example of **correct** code:
```jsx
<div 
  onMouseOver={showTooltip}
  onFocus={showTooltip}
/>
<button
  onMouseOut={hideMenu}
  onBlur={hideMenu}
/>
```