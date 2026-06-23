Pattern: Event handler on non-interactive element

Issue: -

## Description

Non-interactive elements such as `<main>`, `<h1>`, `<p>`, `<img>`, `<li>`, `<ul>`, and
`<ol>` represent content or containers. Adding interaction handlers to them can make the
UI difficult or impossible to operate with assistive technology.

Move the handler to an interactive element, such as `<button>` or `<a href>`, or use an
element with an appropriate interactive role and keyboard behavior.

## Examples

Example of **incorrect** code:
```jsx
<li onClick={() => {}} />
<div role="listitem" onKeyDown={() => {}} />
```

Example of **correct** code:
```jsx
<button onClick={() => {}} />
<div role="button" onClick={() => {}} />
<div onClick={() => {}} role="presentation" />
```
