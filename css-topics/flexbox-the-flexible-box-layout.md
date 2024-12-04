
# Flexbox: Advanced Layout Techniques

Flexbox is a CSS layout model that allows you to design complex layouts easily and efficiently. It provides a way to align and distribute space among items in a container, even when their size is unknown or dynamic. Flexbox is direction-agnostic, which makes it a great choice for many web design scenarios, from simple centering of elements to sophisticated responsive layouts.

## Key Concepts

Before diving into Flexbox, it's important to understand its two main components:

- **Flex Container**: The parent element in which flex items are placed. It defines the layout's structure.
- **Flex Items**: The children elements placed inside the flex container.

![Flex Container and Items](https://dab1nmslvvntp.cloudfront.net/wp-content/uploads/2014/07/1404915977flex-container-and-elements.png)

Flexbox is designed to provide flexibility in two main directions, referred to as axes:

- **Main Axis**: The primary axis along which flex items are laid out.
- **Cross Axis**: The axis perpendicular to the main axis.

![Directions in Flexbox](https://css-tricks.com/wp-content/uploads/2018/11/00-basic-terminology.svg)

The default direction is horizontal (row), but this can be changed easily.

## Starting with a Simple Example

Consider a simple scenario where we have several boxes within a container:

```html
<div class="container">
  <div class="box">1</div>
  <div class="box">2</div>
  <div class="box">3</div>
  <div class="box">4</div>
</div>
```

```css
.container {
  display: flex;
  background-color: #333;
}

.box {
  width: 300px;
  height: 300px;
  color: white;
  font-size: 60px;
  background-color: orange;
  margin: 5px;
}
```

**In this setup, the boxes are laid out horizontally by default, starting from the left.**

## Flexbox Properties for the Container

### `flex-direction`

This property defines the direction of the main axis and can significantly alter the layout's flow:

```css
.container {
  flex-direction: row | row-reverse | column | column-reverse;
}
```

- **row**: Default. Items are placed left to right.
- **row-reverse**: Items are placed right to left.
- **column**: Items are stacked vertically, top to bottom.
- **column-reverse**: Items are stacked bottom to top.

![Flex Direction](https://css-tricks.com/wp-content/uploads/2018/10/flex-direction.svg)

### `flex-wrap`

Controls whether the flex container is single-line or multi-line, and the direction of the cross axis:

```css
.container {
  flex-wrap: nowrap | wrap | wrap-reverse;
}
```

- **nowrap**: Default. All items on one line.
- **wrap**: Items wrap onto multiple lines, from top to bottom.
- **wrap-reverse**: Items wrap onto multiple lines, from bottom to top.

![Flex Wrap](https://css-tricks.com/wp-content/uploads/2018/10/flex-wrap.svg)

### `justify-content`

Aligns items along the main axis and manages space between them:

```css
.container {
  justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly;
}
```

- **flex-start**: Items are aligned to the start of the container.
- **flex-end**: Items are aligned to the end of the container.
- **center**: Items are centered along the line.
- **space-between**: Items are evenly distributed; the first item is at the start, the last item at the end.
- **space-around**: Items are evenly distributed with equal space around each item.
- **space-evenly**: Items are evenly distributed with equal space between the lines.

![Justify Content](https://css-tricks.com/wp-content/uploads/2018/10/justify-content.svg)

### `align-items`

Aligns items along the cross axis:

```css
.container {
  align-items: stretch | flex-start | flex-end | center | baseline;
}
```

- **stretch**: Default. Items are stretched to fill the container.
- **flex-start**: Items are aligned to the start of the cross axis.
- **flex-end**: Items are aligned to the end of the cross axis.
- **center**: Items are centered in the cross axis.
- **baseline**: Items are aligned such as their baselines align.

![Align Items](https://css-tricks.com/wp-content/uploads/2018/10/align-items.svg)

### `align-content`

This property aligns a flex container’s lines within the container when there is extra space on the cross-axis. This property only has an effect when there are multiple lines of flex items:

```css
.container {
  align-content: flex-start | flex-end | center | space-between | space-around | stretch;
}
```

- **flex-start**: Lines are packed toward the start of the flex container.
- **flex-end**: Lines are packed toward the end of the flex container.
- **center**: Lines are centered in the flex container.
- **space-between**: Lines are evenly distributed; the first line is at the start of the container and the last line at the end.
- **space-around**: Lines are evenly distributed with equal space around each line.
- **stretch**: Lines stretch to take up the remaining space.

![Align Content](https://css-tricks.com/wp-content/uploads/2018/10/align-content.svg)

## Properties for the Children (Flex Items)

### `order`

The `order` property controls the order in which flex items appear in the flex container, overriding the source order:

```css
.item1 { order: 2; }
.item2 { order: 1; }
```

Flex items with a lower order are placed before those with a higher order.

### `flex-grow`

This property defines the ability of a flex item to grow if necessary. It accepts a unitless value that serves as a proportion:

```css
.item {
  flex-grow: 1; /* Default is 0 */
}
```

If all items have `flex-grow` set to 1, the remaining space in the container will be distributed equally among all children.

![Flex Grow](https://css-tricks.com/wp-content/uploads/2018/10/flex-grow.svg)

### `flex-shrink`

This defines the ability of a flex item to shrink if necessary:

```css
.item {
  flex-shrink: 1; /* Default is 1 */
}
```

Items will shrink when necessary to prevent overflow.

### `align-self`

This property allows the default alignment (or the one specified by `align-items`) to be overridden for individual flex items:

```css
.item {
  align-self: auto | flex-start | flex-end | center | baseline | stretch;
}
```

- **auto**: Inherits the same as the value of `align-items` property on the parent.
- **flex-start**: Aligns the item to the start of the cross axis.
- **flex-end**: Aligns the item to the end of the cross axis.
- **center**: Centers the item on the cross axis.
- **baseline**: Aligns the item such as their baselines align.
- **stretch**: Items are stretched to fill the container (still respect min-width/max-width).

![Align Self](https://css-tricks.com/wp-content/uploads/2018/10/align-self.svg)