Pattern: Ignored backreference in regular expression

Issue: -

## Description

Backreferences in regular expressions are used to match the same text as previously matched by a capturing group. A backreference is useless when it refers to a group that cannot have matched anything at the time the backreference is evaluated, making the pattern confusing and potentially incorrect.

## Examples

Example of **incorrect** code:
```javascript
/\1(a)/; // backreference appears before group
/(a|\1b)/; // group and reference are in different alternatives
/(?<=\1(a))b/; // backreference used before group in lookbehind
/\1(?!(a))/; // group is inside negative lookahead
/(a\1)/; // backreference is inside its own group
```

Example of **correct** code:
```javascript
/(a)\1/; // valid — backreference follows completed group
/(?<name>a)\k<name>/; // named group used properly
/(?:a|(b))\1/; // backreference only used when group matches
```