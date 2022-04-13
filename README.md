# Mouse Coordinates with CSS Vars

## Description

This demo shows how to use CSS variables to access mouse coordinates.

First and most important, mouse coordinates are not available in CSS yet, the values are provided by script. So keep in mind to have a non script support fallback.

For mobile devices, mouse move events are not supported yet, so you can't use this demo on mobile devices. However, touch events are converted to mouse clicks, so mouse clicks will provide coordinates on the touch of screen.

Finally, the implementation is made with Svelte, but it could be easily converted to vanilla JS.

## Demo
[Live Demo](https://mouse-coordinates-with-css-vars.vercel.app/)

## Install

```bash
npm install
```
## Run

```bash
npm run dev -- --open
```

## License

MIT