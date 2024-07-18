# Project Documentation

## Overview

This project demonstrates a simple HTML and CSS setup to create a horizontal scrolling animation of items within a wrapper. Each item has a delay applied to its animation, creating a sequential scrolling effect.

## HTML Structure

The HTML structure consists of a basic document setup with a series of `div` elements representing items inside a wrapper.

```html
<div class="wrapper">
  <div class="item item-delay" style="--index: 1"></div>
  <div class="item item-delay" style="--index: 2"></div>
  <div class="item item-delay" style="--index: 3"></div>
  <div class="item item-delay" style="--index: 4"></div>
  <div class="item item-delay" style="--index: 5"></div>
  <div class="item item-delay" style="--index: 6"></div>
  <div class="item item-delay" style="--index: 7"></div>
  <div class="item item-delay" style="--index: 8"></div>
</div>
```

### Explanation:
- `<div class="wrapper">`: The main container for the scrolling items. This div element serves as the wrapper for all the items, containing the overall structure and positioning for the animation.
- `<div class="item item-delay" style="--index: X"></div>`: Individual items with an index for delay. These div elements represent the items to be animated. Each item has a unique index to stagger the animation delay, creating a sequential scrolling effect.

## CSS Styles

The CSS provides styling and animation for the items within the wrapper.

```css
body {
  min-height: 100vh;
}

.wrapper {
  height: 100px;
  margin-inline: auto;
  position: relative;
  overflow: hidden;
  mask-image: linear-gradient(
    to right,
    rgba(0, 0, 0, 0),
    rgba(0, 0, 0, 1) 20%,
    rgba(0, 0, 0, 1) 80%,
    rgba(0, 0, 0, 0)
  );
}

@keyframes scroll {
  to {
    left: -200px;
  }
}

.item {
  width: 200px;
  height: 100px;
  background-color: blue;
  border-radius: 6px;
  position: absolute;
  left: calc(200px * 8);
  color: white;
  animation-name: scroll;
  animation-timing-function: linear;
  animation-iteration-count: infinite;
  animation-duration: 30s;
}

.item-delay {
  content: var(--index);
  animation-delay: calc(30s / 8 * (8 - var(--index)) * -1);
}
```

### Explanation:
- `body`: Ensures the body takes up at least the full viewport height.
    - `min-height: 100vh`: Sets the minimum height to the full viewport height to ensure the page covers the entire screen.
- `.wrapper`: Styles for the container holding the items.
    - `height: 100px;`: Sets the height of the wrapper.
    - `margin-inline: auto;`: Centers the wrapper horizontally within the viewport.
    - `position: relative;`: Positions the wrapper relative to its normal position, enabling absolute positioning of child elements.
    - `overflow: hidden;`: Hides any content that overflows the wrapper's boundaries, creating a clean scrolling effect.
    - `mask-image: linear-gradient(...);`: Creates a gradient mask effect to fade the edges of the wrapper, enhancing the visual appeal of the scrolling items.
- `@keyframes scroll`: Defines the keyframes for the scrolling animation.
    - `to { left: -200px; }`: Moves the items to the left by 200px over the animation duration, creating the scrolling effect.
- `.item`: Styles for individual items.
    - `width: 200px;`: Sets the width of each item.
    - `height: 100px;`: Sets the height of each item.
    - `background-color: blue;`: Sets the background color of the items.
    - `border-radius: 6px;`: Rounds the corners of the items for a smoother appearance.
    - `position: absolute;`: Positions the items absolutely within the wrapper, enabling precise control over their placement.
    - `left: calc(200px * 8);`: Positions each item 200px apart horizontally.
    - `color: white;`: Sets the text color of the items to white for better contrast.
    - `animation-name: scroll;`: Applies the scroll animation defined in the @keyframes rule.
    - `animation-timing-function: linear;`: Ensures the animation progresses at a constant speed.
    - `animation-iteration-count: infinite;`: Makes the animation repeat indefinitely.
    - `animation-duration: 30s;`: Sets the duration of the animation to 30 seconds, creating a smooth scrolling effect.
- `.item-delay`: Applies a delay to the animation based on the index.
    - `content: var(--index);`: Uses a CSS variable to set the content of each item based on its index, ensuring unique identification.
    - `animation-delay: calc(30s / 8 * (8 - var(--index)) * -1);`: Calculates the delay for each item's animation based on its index, creating a staggered scrolling effect. This ensures that each item starts scrolling at a different time, enhancing the visual appeal.
