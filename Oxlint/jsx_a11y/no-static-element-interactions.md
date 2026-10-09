Pattern: Event handler on static element without role

Issue: -

## Description

Static HTML elements do not have semantic meaning in accessibility contexts.
When these elements receive click or keyboard event handlers, they must declare a role
to indicate their interactive purpose to assistive technologies.

## Examples

Example of **incorrect** code:
```jsx
<div onClick={() => {}} />
<span onKeyDown={handleKeyDown} />
```

Example of **correct** code:
```jsx
<button onClick={() => {}} />
<div onClick={() => {}} role="button" />
<input type="text" onClick={() => {}} />
```
