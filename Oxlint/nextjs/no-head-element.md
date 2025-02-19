Pattern: HTML head element

Issue: -

## Description

The HTML head element should not be used directly in Next.js applications. Use the Head component from next/head instead to properly manage head elements across pages.

## Examples

Example of **incorrect** code:
```jsx
export default function Page() {
  return (
    <div>
      <head>
        <title>Page Title</title>
      </head>
      <div>Content</div>
    </div>
  )
}
```

Example of **correct** code:
```jsx
import Head from 'next/head'

export default function Page() {
  return (
    <div>
      <Head>
        <title>Page Title</title>
      </Head>
      <div>Content</div>
    </div>
  )
}
```