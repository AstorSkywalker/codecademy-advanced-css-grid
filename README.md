# Codecademy Advanced CSS Grid

A compact learning repository for practicing advanced CSS Grid properties and layout techniques from Codecademy.

**Repository:** [https://github.com/AstorSkywalker/codecademy-advanced-css-grid](https://github.com/AstorSkywalker/codecademy-advanced-css-grid)  
**Live Demo:** [https://astorskywalker.github.io/codecademy-advanced-css-grid](https://astorskywalker.github.io/codecademy-advanced-css-grid)

## Table of Contents
- [Introduction](#introduction)
- [Layouts Included](#layouts-included)
- [Bento Box Layout](#bento-box-layout)
- [Overlapping Grid Items](#overlapping-grid-items)
- [Justify Items Example](#justify-items-example)
- [Project Structure](#project-structure)
- [Resources](#resources)

## Introduction

This repository documents a learning journey through advanced CSS Grid. The project focuses on three practical patterns that are useful when building modern responsive interfaces:

- Named grid areas for structured layouts
- Overlapping items with explicit grid line placement
- Horizontal alignment inside grid cells with `justify-items`

## Layouts Included

### 1. Bento Box Layout

The main demo uses `grid-template-areas` to create a bento-style layout with a hero panel, supporting feature cards, and a wide content area.

### 2. Overlapping Grid Items

The second demo uses line-based placement and `z-index` to show how grid items can overlap while still being controlled by the grid.

### 3. Justify Items Example

The secondary page uses narrow child items to make the effect of `justify-items: start` clearly visible.

## Bento Box Layout

Bento layouts are visually asymmetrical but still highly organized. CSS Grid makes them easier to build by naming layout regions with `grid-template-areas`.

### Visual Layout Diagram

```text
+-----------------+-------------+
|                 |  Feature 1  |
|                 |             |
|    Hero Image   +-------------+
|                 |  Feature 2  |
|                 |             |
+-----------------+-------------+
|   Wide Content  |  Feature 3  |
+-----------------+-------------+
```

### Grid Template Areas

```css
grid-template-areas:
  "hero hero feature1"
  "hero hero feature2"
  "wide wide feature3";
```

This creates:

- Three equal-width columns with `repeat(3, 1fr)`
- Three fixed-height rows with `repeat(3, 200px)`
- A hero area that spans two columns and two rows
- Two stacked feature cards on the right
- A wide content panel at the bottom left

### Core HTML

```html
<div class="bento-container">
  <div class="item item-1">Hero Image</div>
  <div class="item item-2">Feature 1</div>
  <div class="item item-3">Feature 2</div>
  <div class="item item-4">Feature 3</div>
  <div class="item item-5">Wide Content</div>
</div>
```

### Responsive Behavior

On smaller screens, the bento layout switches to a single-column stack so each area remains readable and easy to scan.

```css
@media (max-width: 768px) {
  .bento-container {
    grid-template-columns: 1fr;
    grid-template-rows: auto;

    grid-template-areas:
      "hero"
      "feature1"
      "feature2"
      "feature3"
      "wide";
  }
}
```

## Overlapping Grid Items

This example uses explicit grid line coordinates instead of named areas:

```css
.item-6 {
  grid-area: 1 / 1 / 3 / 3;
  z-index: 2;
}

.item-7 {
  grid-area: 1 / 3 / 3 / 5;
  z-index: 1;
}

.item-8 {
  grid-area: 2 / 2 / 4 / 4;
  z-index: 3;
}
```

Key concepts demonstrated:

- Positioning with row and column grid lines
- Spanning multiple rows and columns
- Layering items with `z-index`
- Creating depth and visual hierarchy inside a grid

## Justify Items Example

The justify-items demo focuses on alignment inside each grid cell:

```css
.justified-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  justify-items: start;
}

.item-9,
.item-10,
.item-11 {
  width: 50px;
}
```

Because the items are narrower than their columns, `justify-items: start` makes the left alignment obvious.

## Project Structure

- `index.html`: main showcase page for the bento-box and overlapping-grid examples
- `justified.html`: separate page dedicated to the `justify-items` example
- `style.css`: shared layout, color, spacing, and responsive styles
- `README.md`: documentation for the learning examples in this repository

## Resources

- [MDN: grid-template-areas](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-areas)
- [MDN: grid-area](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-area)
- [MDN: justify-items](https://developer.mozilla.org/en-US/docs/Web/CSS/justify-items)
- [CSS-Tricks: A Complete Guide to Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)
- [Codecademy Advanced CSS Grid Lesson](https://www.codecademy.com/journeys/front-end-engineer/paths/fecj-22-improved-styling-with-css/tracks/fecj-22-making-a-website-responsive/modules/wdcp-22-learn-css-grid-5f3cef21-7a34-415b-beef-3207850da2ce/lessons/advanced-css-grid/exercises/introduction)

---
Last updated: March 27, 2026
