Pattern: Internal navigation without `resolve()`

Issue: -

## Description

This rule ensures internal navigation via HTML `<a>` tags, SvelteKit’s `goto()`, `pushState(`) and `replaceState()` uses `resolve()`. `<a>` tags will skip this check when it has an absolute URL or rel="external". For programmatic external navigation, use `window.location`. Enforcing this rule ensures the base path is prefixed and internal links are type-checked.

```svelte

<!-- ✓ GOOD -->
<script>
  /* eslint svelte/no-navigation-without-resolve: "error" */

  import { goto, pushState, replaceState } from '$app/navigation';
  import { resolve } from '$app/paths';

  goto(resolve('/foo/'));
  pushState(resolve('/foo/'), {});
  replaceState(resolve('/foo/'), {});

  // shallow routing
  pushState('', {});
  replaceState('', {});
</script>

<a href={resolve('/foo/')}>Click me!</a>
<a href="https://svelte.dev">Click me!</a>
<a href={someURL} rel="external">Click me!</a>
<a href="#top">Click me!</a>

<!-- ✗ BAD -->
<script>
  /* eslint svelte/no-navigation-without-resolve: "error" */

  import { goto, pushState, replaceState } from '$app/navigation';
  import { resolve } from '$app/paths';

  goto('/foo');
  goto('/foo' + resolve('/bar'));
  goto(resolve('/foo') + '/bar');

  pushState('/foo', {});
  replaceState('/foo', {});
</script>

<a href="/foo">Click me!</a>
<a href={'/foo'}>Click me!</a>
```
