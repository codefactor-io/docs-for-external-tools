Pattern: Plain script for Google Analytics

Issue: -

## Description

Google Analytics scripts should use Next.js's Script component with the strategy prop set appropriately. This ensures proper loading and execution timing for analytics code.

## Examples

Example of **incorrect** code:
```jsx
<script async src="https://www.googletagmanager.com/gtag/js?id=GA_ID" />
```

Example of **correct** code:
```jsx
import Script from 'next/script'

<Script
  src="https://www.googletagmanager.com/gtag/js?id=GA_ID"
  strategy="afterInteractive"
/>
```