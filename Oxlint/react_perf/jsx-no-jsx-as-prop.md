Pattern: Inline JSX creation in props

Issue: -

## Description

Using locally defined JSX elements as prop values leads to unnecessary re-renders since a new element instance is created on each parent render. This causes child components to re-render and makes props harder to maintain consistently.

## Examples

Example of **incorrect** code:
```jsx
<Item jsx={<SubItem />} />
<Item jsx={this.props.jsx || <SubItem />} />
<Item jsx={this.props.jsx ? this.props.jsx : <SubItem />} />
```

Example of **correct** code:
```jsx
<Item callback={this.props.jsx} />
```