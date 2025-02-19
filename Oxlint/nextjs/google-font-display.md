Pattern: Missing font-display strategy

Issue: -

## Description

Google Fonts links should include a display parameter to control font loading behavior. Using display=optional or display=swap helps prevent invisible text and layout shifts during font loading.

## Examples

Example of **incorrect** code:
```jsx
<link 
  href="https://fonts.googleapis.com/css2?family=Roboto" 
  rel="stylesheet" 
/>
```

Example of **correct** code:
```jsx
<link 
  href="https://fonts.googleapis.com/css2?family=Roboto&display=optional" 
  rel="stylesheet"
/>
```