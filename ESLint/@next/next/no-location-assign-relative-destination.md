Pattern: Use of `location` for internal navigation

Issue: -

## Description

Using `location.assign()` or assigning to `location.href` with a relative URL bypasses the Next.js router. This reloads the page instead of performing a client-side transition, discarding prefetched data and application state.

Use `redirect()` from `next/navigation` during rendering, or `useRouter().push()` in client-side event handlers. Browser location APIs can still be used to navigate to external URLs.

## Examples

Example of **incorrect** code:

```jsx
"use client";

export default function SettingsButton() {
  return (
    <button onClick={() => location.assign("/settings")}>
      Open settings
    </button>
  );
}
```

Example of **correct** code:

```jsx
"use client";

import { useRouter } from "next/navigation";

export default function SettingsButton() {
  const router = useRouter();

  return (
    <button onClick={() => router.push("/settings")}>
      Open settings
    </button>
  );
}
```

## Further Reading

* [Next.js - No location.assign or location.href navigation to relative URLs](https://nextjs.org/docs/messages/no-location-assign-relative-destination)
