Pattern: Distracting element

Issue: -

## Description

Visually distracting elements like <marquee> and <blink> can cause accessibility issues for users with visual impairments or cognitive disabilities. These elements are deprecated and should not be used.

## Examples

Example of **incorrect** code:
```jsx
<marquee>Scrolling text</marquee>
<blink>Flashing text</blink>
```

Example of **correct** code:
```jsx
<div className="announcement">Important text</div>
<span className="highlight">Emphasized text</span>
```