# CSS and tailwind

## History of CSS

https://www.youtube.com/watch?v=UvF0Zt4_NGU

## Positioning HTML Elements with CSS

### Flexbox

Flexbox, or Flexible Box Layout, is a CSS3 web layout model. It's great for designing flexible responsive layout structure without using float or positioning.

To use Flexbox:
1. Set the container element to display: flex; This makes the direct children of the container become flex items.

```
.container {
  display: flex;
}

```

2. Use properties like justify-content, align-items, and flex-direction to adjust the layout of these items.

```
.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-direction: row;
}

```

### Grid
CSS Grid Layout is a 2-dimensional system, meaning it can handle both columns and rows. This makes it very powerful for building complex web layouts.

To use Grid:
1. Set the container element to display: grid;

```
.container {
  display: grid;
}
```
2. Use properties like grid-template-columns, grid-template-rows, and grid-gap to define the structure of your grid.

```
.container {
  display: grid;
  grid-template-columns: 1fr 2fr;
  grid-template-rows: auto;
  grid-gap: 20px;
}
```
## Tailwind

https://youtu.be/Ksn1tThNTjI?si=F5L28-mxy3VpA4mT

## Further reading
1. [Basic concepts of flexbox - CSS: Cascading Style Sheets | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_flexible_box_layout/Basic_concepts_of_flexbox)
2. [A Complete Guide to Flexbox | CSS-Tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
3. [A Complete Guide to CSS Grid | CSS-Tricks](https://css-tricks.com/snippets/css/complete-guide-grid/)
4. [CSS grid layout - CSS: Cascading Style Sheets | MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_grid_layout)