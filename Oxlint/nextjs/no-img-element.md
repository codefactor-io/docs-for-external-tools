Pattern: HTML img element

Issue: -

## Description

The HTML img element should not be used directly in Next.js applications. Use the Image component from next/image instead to get automatic image optimization, responsive images, and better performance.

## Examples

Example of **incorrect** code:
```jsx
export default function Page() {
  return (
    <div>
      <img src="/photo.jpg" alt="Photo" />
    </div>
  )
}
```

Example of **correct** code:
```jsx
import Image from 'next/image'

export default function Page() {
  return (
    <div>
      <Image
        src="/photo.jpg"
        alt="Photo"
        width={500}
        height={300}
      />
    </div>
  )
}
```