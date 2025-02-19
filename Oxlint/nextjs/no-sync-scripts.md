Pattern: Synchronous script tag

Issue: -

## Description

Synchronous script tags block the page rendering and should be avoided in Next.js applications. Use the Script component from next/script instead for better performance and control over script loading.

## Examples

Example of **incorrect** code:
```jsx
<head>
  <script src="/analytics.js" />
  <script>{`console.log('inline')`}</script>
</head>
```

Example of **correct** code:
```jsx
import Script from 'next/script'

export default function Page() {
  return (
    <>
      <Script src="/analytics.js" strategy="afterInteractive" />
      <Script id="inline">{`console.log('inline')`}</Script>
    </>
  )
}
```