Pattern: Async client component

Issue: -

## Description

Client components in Next.js should not be async functions. Async components can cause hydration issues and unexpected behavior. Use hooks or other patterns for async operations in client components.

## Examples

Example of **incorrect** code:
```jsx
'use client'

async function ClientComponent() {
  const data = await fetchData()
  return <div>{data}</div>
}
```

Example of **correct** code:
```jsx
'use client'

function ClientComponent() {
  const [data, setData] = useState(null)
  
  useEffect(() => {
    fetchData().then(setData)
  }, [])
  
  return <div>{data}</div>
}
```