Pattern: Redundant image alt text

Issue: -

## Description

Alt text should not include words like "image", "picture", or "photo" since screen readers already announce that the element is an image. Redundant words make the experience more verbose for screen reader users.

## Examples

Example of **incorrect** code:
```jsx
<img src="cat.jpg" alt="Image of a cat playing" />
<img src="dog.jpg" alt="Photo of a dog sleeping" />
<img src="bird.jpg" alt="Picture of a bird flying" />
```

Example of **correct** code:
```jsx
<img src="cat.jpg" alt="Cat playing with yarn" />
<img src="dog.jpg" alt="Golden retriever sleeping on couch" />
<img src="bird.jpg" alt="Blue jay in flight" />
```