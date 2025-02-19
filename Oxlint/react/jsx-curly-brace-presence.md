Pattern: Unnecessary curly braces in JSX

Issue: -

## Description

JSX allows string literals to be written without curly braces. Using unnecessary curly braces around string literals reduces code readability. However, curly braces are required for expressions, template literals with interpolation, and strings containing certain characters.

## Examples

Example of **incorrect** code:
```jsx
<App>{"Hello world"}</App>;
<App prop={"Hello world"} attr={"foo"} />;
```

Example of **correct** code:
```jsx
<App>Hello world</App>;
<App prop="Hello world" attr="foo" />;
<App>{`Hello ${name}`}</App>;
<App prop={'Hello "world"'} />;
```