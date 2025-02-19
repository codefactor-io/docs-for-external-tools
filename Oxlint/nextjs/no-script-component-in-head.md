Pattern: Script component in Head

Issue: -

## Description

The next/script component should not be placed within next/head. Scripts should be placed directly in the body of the document to ensure proper loading and execution.

## Examples

Example of **incorrect** code:
```jsx
import Head from 'next/head'
import Script from 'next/script'

export default function Page() {
  return (
    <Head>
      <Script src="/analytics.js" />
    </Head>
  )
}
```

Example of **correct** code:
```jsx
import Head from 'next/head'
import Script from 'next/script'

export default function Page() {
  return (
    <>
      <Head />
      <Script src="/analytics.js" />
    </>
  )
}
```