Pattern: Violation of React Hooks rules

Issue: -

## Description

React Hooks must follow specific rules: only call hooks at the top level of your component, not inside loops, conditions, or nested functions, and only call hooks from React function components or custom hooks.

## Examples

Example of **incorrect** code:
```jsx
function Counter() {
  if (condition) {
    const [count, setCount] = useState(0); // Hook inside condition
  }
  
  function handleClick() {
    useEffect(() => {}); // Hook inside nested function
  }
}
```

Example of **correct** code:
```jsx
function Counter() {
  const [count, setCount] = useState(0);
  
  useEffect(() => {
    // Side effect code
  }, []);
  
  if (condition) {
    // Regular code
  }
}
```