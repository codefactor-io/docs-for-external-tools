Pattern: Negation of left operand in relational expression

Issue: -

## Description

Negating the left operand of `in` or `instanceof` operators is usually a mistake. Due to operator precedence, `!key in object` is evaluated as `(!key) in object`, when the intent was likely `!(key in object)`. Similar issues occur with instanceof.

## Examples

Example of **incorrect** code:
```javascript
if (!key in object) {
  // Evaluated as (!key) in object
}

if (!obj instanceof Class) {
  // Evaluated as (!obj) instanceof Class
}

if (!a in b && !c in d) {
  // Multiple unsafe negations
}

const result = !number in range;
```

Example of **correct** code:
```javascript
if (!(key in object)) {
  // Properly negates membership test
}

if (!(obj instanceof Class)) {
  // Properly negates instance check
}

const result = !(number in range);

// Or rewrite without negation
if (obj instanceof Class === false) {
  // Alternative to negation
}
```