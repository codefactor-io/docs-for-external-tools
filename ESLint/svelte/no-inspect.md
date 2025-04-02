Pattern: Use of `$inspect` directive

Issue: -

## Description

This rule reports usages of `$inspect`.

```svelte
<script>
  /* eslint svelte/no-inspect: "error" */
  // ✗ BAD
  $inspect(1);
</script>
```