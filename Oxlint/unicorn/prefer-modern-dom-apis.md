Pattern: Legacy DOM manipulation method 

Issue: -

## Description

Modern DOM APIs provide more convenient methods for node manipulation that don't require accessing parent nodes and support multiple operations at once. Use `replaceWith()`, `before()`, and modern adjacency methods instead of legacy alternatives like `replaceChild()` and `insertBefore()`.

## Examples

Example of **incorrect** code:
```javascript
parentNode.replaceChild(newChildNode, oldChildNode);
parentNode.insertBefore(newNode, referenceNode);
referenceNode.insertAdjacentText('beforebegin', 'text');
```

Example of **correct** code:
```javascript
oldChildNode.replaceWith(newChildNode);
referenceNode.before(newNode);
referenceNode.before('text');
```