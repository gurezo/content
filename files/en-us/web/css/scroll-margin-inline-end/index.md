---
title: scroll-margin-inline-end
slug: Web/CSS/scroll-margin-inline-end
page-type: css-property
browser-compat: css.properties.scroll-margin-inline-end
sidebar: cssref
---

The `scroll-margin-inline-end` property defines the margin of the scroll snap area at the end of the inline dimension that is used for snapping this box to the [snapport](/en-US/docs/Glossary/Scroll_snap#snapport). The scroll snap area is determined by taking the transformed border box, finding its rectangular bounding box (axis-aligned in the scroll container's coordinate space), then adding the specified outsets.

{{InteractiveExample("CSS Demo: scroll-margin-inline-end")}}

```css interactive-example-choice
scroll-margin-inline-end: 0;
```

```css interactive-example-choice
scroll-margin-inline-end: 20px;
```

```css interactive-example-choice
scroll-margin-inline-end: 2em;
```

```html interactive-example
<section class="default-example" id="default-example">
  <div class="scroller">
    <div>1</div>
    <div id="example-element">2</div>
    <div>3</div>
  </div>
  <div class="info">Scroll »</div>
</section>
```

```css interactive-example
.default-example {
  flex-wrap: wrap;
}

.default-example .info {
  width: 100%;
  padding: 0.5em 0;
  font-size: 90%;
}

.scroller {
  text-align: left;
  width: 250px;
  height: 250px;
  overflow-x: scroll;
  display: flex;
  box-sizing: border-box;
  border: 1px solid black;
  scroll-snap-type: x mandatory;
}

.scroller > div {
  flex: 0 0 250px;
  width: 250px;
  background-color: rebeccapurple;
  color: #fff;
  font-size: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
  scroll-snap-align: end;
}

.scroller > div:nth-child(even) {
  background-color: #fff;
  color: rebeccapurple;
}
```

## Syntax

```css
/* <length> values */
scroll-margin-inline-end: 10px;
scroll-margin-inline-end: 1em;

/* Global values */
scroll-margin-inline-end: inherit;
scroll-margin-inline-end: initial;
scroll-margin-inline-end: revert;
scroll-margin-inline-end: revert-layer;
scroll-margin-inline-end: unset;
```

### Values

- {{CSSXref("&lt;length&gt;")}}
  - : An outset from the inline end edge of the scroll container.

## Formal definition

{{cssinfo}}

## Formal syntax

{{csssyntax}}

## Examples

### Basic demonstration

This example implements something very similar to the interactive example above, except that here we'll explain to you how it's implemented.

The aim here is to create four horizontally-scrolling blocks, the second and third of which snap into place, near but not quite at the right of each block.

#### HTML

The HTML includes a scroller with four children:

```html
<div class="scroller">
  <div>1</div>
  <div>2</div>
  <div>3</div>
  <div>4</div>
</div>
```

#### CSS

Let's walk through the CSS. The outer container is styled like this:

```css
.scroller {
  text-align: left;
  width: 250px;
  height: 250px;
  overflow-x: scroll;
  display: flex;
  box-sizing: border-box;
  border: 1px solid #000;
  scroll-snap-type: x mandatory;
}
```

The main parts relevant to the scroll snapping are `overflow-x: scroll`, which makes sure the contents will scroll and not be hidden, and `scroll-snap-type: x mandatory`, which dictates that scroll snapping must occur along the horizontal axis, and the scrolling will always come to rest on a snap point.

The child elements are styled as follows:

```css
.scroller > div {
  flex: 0 0 250px;
  width: 250px;
  background-color: #663399;
  color: #fff;
  font-size: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
  scroll-snap-align: end;
}

.scroller > div:nth-child(2n) {
  background-color: #fff;
  color: #663399;
}
```

The most relevant part here is `scroll-snap-align: end`, which specifies that the right-hand edges (the "ends" along the x axis, in our case) are the designated snap points.

Last of all we specify the scroll margin values, a different one for the second and third child elements:

```css
.scroller > div:nth-child(2) {
  scroll-margin-inline-end: 1rem;
}

.scroller > div:nth-child(3) {
  scroll-margin-inline-end: 2rem;
}
```

This means that when scrolling past the middle child elements, the scrolling will snap to `1rem` outside the inline end edge of the second `<div>`, and `2rems` outside the inline end edge of the third `<div>`.

#### Result

Try it for yourself:

{{EmbedLiveSample('Basic_demonstration', '100%', 300)}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [CSS scroll snap](/en-US/docs/Web/CSS/CSS_scroll_snap)
- [Well-controlled scrolling with CSS scroll snap](https://web.dev/articles/css-scroll-snap)
