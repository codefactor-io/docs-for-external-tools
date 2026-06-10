Pattern: Overriding meaning of non-interactive element

Issue: -

## Description

Overriding the semantic meaning of non-interactive elements with interactive roles creates confusion for assistive technology users. The element lacks the expected keyboard interaction patterns and focus management that interactive elements provide.

## Examples

Example of **incorrect** code:

```jsx
<h1 role="button">Click me</h1>
<li role="link">Navigate</li>
<article role="button">Submit</article>
```

Example of **correct** code:

```jsx
<button>Click me</button>
<a href="/page">Navigate</a>
<div role="button">Submit</div>
<ul role="menu"><li role="menuitem">Item</li></ul>
```