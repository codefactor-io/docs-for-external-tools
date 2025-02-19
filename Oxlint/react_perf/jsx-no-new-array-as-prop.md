Pattern: Inline array creation in JSX props

Issue: -

## Description

Using locally defined arrays as prop values leads to unnecessary re-renders since a new array instance is created on each parent render. This causes child components to re-render and makes props harder to maintain consistently.

## Examples

Example of **incorrect** code:
```jsx
<Item list={[]} />
<Item list={new Array()} />
<Item list={Array()} />
<Item list={this.props.list || []} />
<Item list={this.props.list ? this.props.list : []} />
```

Example of **correct** code:
```jsx
<Item list={this.props.list} />
```