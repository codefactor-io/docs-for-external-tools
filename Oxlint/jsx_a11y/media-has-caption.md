Pattern: Media without captions

Issue: -

## Description

Audio and video elements must have captions provided through a track element. Captions ensure media content is accessible to users who are deaf or hard of hearing.

## Examples

Example of **incorrect** code:
```jsx
<video src="tutorial.mp4"></video>
<audio src="podcast.mp3"></audio>
```

Example of **correct** code:
```jsx
<video src="tutorial.mp4">
  <track kind="captions" src="tutorial-captions.vtt" />
</video>

<audio src="podcast.mp3">
  <track kind="captions" src="podcast-captions.vtt" />
</audio>
```