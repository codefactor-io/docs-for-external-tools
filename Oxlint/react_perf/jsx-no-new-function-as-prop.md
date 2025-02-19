Pattern: Inline function creation in JSX props

Issue: -

## Description

Using locally defined functions as prop values leads to unnecessary re-renders since a new function instance is created on each parent render. This causes child components to re-render and makes props harder to maintain consistently.

## Examples

Example of **incorrect** code:
```jsx
<Item callback={new Function(...)} />
<Item callback={this.props.callback || function() {}} />
```

Example of **correct** code:
```jsx
<Item callback={this.props.callback} />
```