# Codecademy Advanced CSS Grid

A comprehensive learning repository for mastering Advanced CSS Grid properties and techniques from Codecademy.

## Table of Contents
- [Introduction](#introduction)
- [Bento Box Layout](#bento-box-layout)
- [Resources](#resources)

## Introduction
This repository documents my learning journey through Advanced CSS Grid. CSS Grid is a powerful layout system for creating complex, responsive designs.

## Bento Box Layout

Bento boxes are a popular modern layout pattern inspired by Japanese bento food containers. They use CSS Grid with `grid-template-areas` to create visually appealing, asymmetrical layouts with items of different sizes.

### Visual Layout Diagram

Here's how our bento box layout will look:

```
┌─────────────────┬─────────────┐
│                 │  Feature 1  │
│                 │             │
│    Hero Image   ├─────────────┤
│                 │  Feature 2  │
│                 │             │
├─────────────────┴─────────────┤
│                               │
│         Wide Content          │
│                               │
└───────────────────────────────┘
```

### Grid Template Areas Explained

The `grid-template-areas` property defines named areas in our grid:

```css
grid-template-areas:
  "hero hero feature1"    /* Row 1: hero spans 2 columns, feature1 takes 1 */
  "hero hero feature2"    /* Row 2: hero spans 2 columns, feature2 takes 1 */
  "wide wide feature3";   /* Row 3: wide spans 2 columns, feature3 takes 1 */
```

**What this creates:**
- **3 columns**: `repeat(3, 1fr)` - three equal-width columns
- **3 rows**: `repeat(3, 200px)` - three 200px-high rows
- **Named areas**:
  - `hero`: spans columns 1-2, rows 1-2 (large top-left area)
  - `feature1`: column 3, row 1 (top-right)
  - `feature2`: column 3, row 2 (middle-right)
  - `feature3`: column 3, row 3 (bottom-right)
  - `wide`: spans columns 1-2, row 3 (bottom-wide area)

### Bento Box Example

**HTML:**
```html
<div class="bento-container">
  <div class="item item-1">Hero Image</div>
  <div class="item item-2">Feature 1</div>
  <div class="item item-3">Feature 2</div>
  <div class="item item-4">Feature 3</div>
  <div class="item item-5">Wide Content</div>
</div>
```

**CSS:**
```css
.bento-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(3, 200px);
  gap: 1rem;
  padding: 2rem;
  max-width: 1200px;
  margin: 0 auto;
  
  grid-template-areas:
    "hero hero feature1"
    "hero hero feature2"
    "wide wide feature3";
}

.item {
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.25rem;
  font-weight: bold;
  color: white;
}

/* Assign areas */
.item-1 {
  grid-area: hero;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}

.item-2 {
  grid-area: feature1;
  background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
}

.item-3 {
  grid-area: feature2;
  background: linear-gradient(135deg, #4facfe 0%, #00f2fe 100%);
}

.item-4 {
  grid-area: feature3;
  background: linear-gradient(135deg, #43e97b 0%, #38f9d7 100%);
}

.item-5 {
  grid-area: wide;
  background: linear-gradient(135deg, #fa709a 0%, #fee140 100%);
}
```

### How It Works
1. **Grid Definition**: `grid-template-columns: repeat(3, 1fr)` creates 3 equal columns
2. **Area Layout**: 
   - `hero` spans 2 columns and 2 rows (left side)
   - `feature1`, `feature2`, `feature3` each take 1 column (right side)
   - `wide` spans all 3 columns (bottom)
3. **Visual Result**: An asymmetrical but balanced layout that showcases content hierarchy

### Key Concepts Demonstrated
- **Spanning**: Items can span multiple rows and columns
- **Named Areas**: Makes the layout structure clear and easy to visualize
- **Flexibility**: Easy to rearrange with media queries
- **Hierarchy**: Larger areas draw attention to important content

### Responsive Version
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

On mobile, all items stack vertically while maintaining their semantic areas.

## Resources
- [MDN: grid-template-areas](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-areas)
- [CSS Tricks: Complete Guide to Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)
- [Codecademy CSS Grid Course](https://codecademy.com)

---
Last updated: March 4, 2026
