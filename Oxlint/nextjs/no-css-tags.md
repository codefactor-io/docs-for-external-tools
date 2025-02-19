Pattern: Direct CSS link tag

Issue: -

## Description

Next.js handles CSS imports automatically and provides built-in CSS support. Using direct link tags for CSS can bypass Next.js's optimization and cause styling issues.

## Examples

Example of **incorrect** code:
```jsx
<Head>
  <link href="/styles.css" rel="stylesheet" />
</Head>
```

Example of **correct** code:
```jsx
// Use CSS imports
import '../styles/global.css'
import styles from '../styles/component.module.css'
```