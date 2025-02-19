Pattern: Use of `alert`, `confirm`, or `prompt`

Issue: -

## Description

The built-in `alert`, `confirm`, and `prompt` functions create obtrusive UI elements that interrupt the user experience. They should be replaced with custom UI components that match the application's design. Additionally, `alert` is often used for debugging and should be removed before deployment.

## Examples

Example of **incorrect** code:
```javascript
alert("here!");
confirm("Are you sure?");
prompt("What's your name?", "John Doe");
```

Example of **correct** code:
```javascript
customAlert("Something happened!");
customConfirm("Are you sure?");
customPrompt("Who are you?");

// Using custom implementation
function foo() {
  const alert = myCustomLib.customAlert;
  alert();
}
```