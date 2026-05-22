Pattern: Missing use of `u`/`v` in regular expression

Issue: -

## Description

Enforce the use of `u` or `v` flag on regular expressions.

RegExp `u` flag has two effects:

    Make the regular expression handling UTF-16 surrogate pairs correctly.
	Make the regular expression throwing syntax errors early as disabling Annex B extensions. 

The RegExp `v` flag, introduced in ECMAScript 2024, is a superset of the `u` flag, and offers two more features:

    Unicode properties of strings.
	Set notation It allows for set operations between character classes.

## Examples

Example of **incorrect** code:

```ts
const a = /aaa/;
const b = /bbb/gi;
const c = new RegExp("ccc");
const d = new RegExp("ddd", "gi");
```

Example of **correct** code:

```ts
const a = /aaa/u;
const b = /bbb/giu;
const c = new RegExp("ccc", "u");
const d = new RegExp("ddd", "giu");

const e = /aaa/v;
const f = /bbb/giv;
const g = new RegExp("ccc", "v");
const h = new RegExp("ddd", "gv");

// This rule ignores RegExp calls if the flags could not be evaluated to a static value.
function i(flags) {
  return new RegExp("eee", flags);
}
```