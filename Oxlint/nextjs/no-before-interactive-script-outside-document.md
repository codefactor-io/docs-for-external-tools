Pattern: Misplaced beforeInteractive script

Issue: -

## Description

Scripts with the beforeInteractive strategy must only be used in pages/_document.js. Using them elsewhere prevents proper script loading and execution timing.

## Examples

Example of **incorrect** code:
```jsx
// pages/index.js
import Script from 'next/script'

export default function Home() {
  return (
    <div>
      <Script src="/script.js" strategy="beforeInteractive" />
    </div>
  )
}
```

Example of **correct** code:
```jsx
// pages/_document.js
import Script from 'next/script'

export default function MyDocument() {
  return (
    <Html>
      <Head>
        <Script src="/script.js" strategy="beforeInteractive" />
      </Head>
      <body>
        <Main />
        <NextScript />
      </body>
    </Html>
  )
}
```