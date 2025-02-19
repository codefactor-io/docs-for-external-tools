Pattern: Use of restricted Jest method

Issue: -

## Description

Some Jest methods may be restricted in a project to enforce consistent testing patterns or avoid problematic testing practices.

## Examples

Example of **incorrect** code:
```javascript
jest.useFakeTimers();
jest.spyOn(video, "play");
jest.advanceTimersByTime(1000);
```

Example of **correct** code:
```javascript
// Use allowed methods based on project configuration
jest.fn();
expect.any(Number);
await waitFor(() => {});
```