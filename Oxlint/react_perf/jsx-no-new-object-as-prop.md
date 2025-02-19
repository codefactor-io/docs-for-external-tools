Pattern: Inline object creation in JSX props

Issue: -

## Description

Using locally defined objects as prop values leads to unnecessary re-renders since a new object instance is created on each parent render. This causes child components to re-render and makes props harder to maintain consistently.

## Examples

Example of **incorrect** code:
```jsx
<Item config={{}} />
<Item config={new Object()} />
<Item config={Object()} />
<Item config={this.props.config || {}} />
<Item config={this.props.config ? this.props.config : {}} />
<div style={{display: 'none'}} />
```

Example of **correct** code:
```jsx
<Item config={staticConfig} />
```