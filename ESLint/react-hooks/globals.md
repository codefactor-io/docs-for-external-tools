Pattern: Assignment/mutation of global during render

Issue: -

## Description

Global variables exist outside React’s control. When you modify them during render, you break React’s assumption that rendering is pure. This can cause components to behave differently in development vs production, break Fast Refresh, and make your app impossible to optimize with features like React Compiler.

Examples of **incorrect** code for this rule:

```jsx
// ❌ Global counter
let renderCount = 0;
function Component() {
  renderCount++; // Mutating global
  return <div>Count: {renderCount}</div>;
}

// ❌ Modifying window properties
function Component({userId}) {
  window.currentUser = userId; // Global mutation
  return <div>User: {userId}</div>;
}

// ❌ Global array push
const events = [];
function Component({event}) {
  events.push(event); // Mutating global array
  return <div>Events: {events.length}</div>;
}

// ❌ Cache manipulation
const cache = {};
function Component({id}) {
  if (!cache[id]) {
    cache[id] = fetchData(id); // Modifying cache during render
  }
  return <div>{cache[id]}</div>;
}
```

Examples of **correct** code for this rule:

```jsx
// ✅ Use state for counters
function Component() {
  const [clickCount, setClickCount] = useState(0);

  const handleClick = () => {
    setClickCount(c => c + 1);
  };

  return (
    <button onClick={handleClick}>
      Clicked: {clickCount} times
    </button>
  );
}

// ✅ Use context for global values
function Component() {
  const user = useContext(UserContext);
  return <div>User: {user.id}</div>;
}

// ✅ Synchronize external state with React
function Component({title}) {
  useEffect(() => {
    document.title = title; // OK in effect
  }, [title]);

  return <div>Page: {title}</div>;
}
```