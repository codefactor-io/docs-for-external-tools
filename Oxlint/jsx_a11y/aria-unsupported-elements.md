Pattern: ARIA on unsupported element

Issue: -

## Description

Certain DOM elements like meta, html, script, and style do not support ARIA attributes because they are not visible or interactive. Adding ARIA roles or properties to these elements has no effect.

## Examples

Example of **incorrect** code:
```jsx
<meta charset="UTF-8" aria-hidden="true" />
<html role="application" />
<script aria-label="script" />
<style role="text" />
```

Example of **correct** code:
```jsx
<meta charset="UTF-8" />
<html lang="en" />
<script type="text/javascript" />
<style type="text/css" />
```