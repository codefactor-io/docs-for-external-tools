Pattern: Unnecessary children snippet

Issue: -

## Description

Any content inside component tags that is not a snippet declaration implicitly becomes part of the children snippet. Thus, declaring the children snippet explicitly is only necessary when the snippet has parameters.

## Examples

```svelte
<script>
  /* eslint svelte/no-useless-children-snippet: "error" */

  import { Foo } from './Foo.svelte';
</script>

<!-- ✓ GOOD -->
<Foo>
  {#snippet bar()}
    Hello
  {/snippet}
</Foo>

<Foo>
  {#snippet children(val)}
    Hello {val}
  {/snippet}
</Foo>

<Foo>Hello</Foo>

<!-- ✗ BAD -->
<Foo>
  

{#snippet children()}
    Hello
  {/snippet}
</Foo>
```
