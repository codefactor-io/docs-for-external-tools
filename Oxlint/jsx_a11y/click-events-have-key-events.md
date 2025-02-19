Pattern: Click handler without keyboard event

Issue: -

## Description

Elements with onClick handlers must also have keyboard event handlers (onKeyUp, onKeyDown, or onKeyPress) to ensure keyboard-only users can access all functionality. This requirement does not apply to interactive elements like buttons.

## Examples

Example of **incorrect** code:
```jsx
<div onClick={handleClick} />
<span onClick={activate} role="button" />
```

Example of **correct** code:
```jsx
<div 
  onClick={handleClick}
  onKeyDown={handleKeyDown}
/>
<button onClick={activate} />
```