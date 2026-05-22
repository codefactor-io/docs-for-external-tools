Pattern: Use of `flushSync`

Issue: -

## Description

`flushSync` can significantly hurt performance and may unexpectedly force pending Suspense boundaries to show their fallback state.

Most of the time, `flushSync` can be avoided, so use `flushSync` as a last resort.