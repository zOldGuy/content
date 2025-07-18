---
title: left
slug: Web/CSS/left
page-type: css-property
browser-compat: css.properties.left
---

{{CSSRef}}

The **`left`** [CSS](/en-US/docs/Web/CSS) property participates in specifying the horizontal position of a [positioned element](/en-US/docs/Web/CSS/position). This {{glossary("inset properties", "inset property")}} has no effect on non-positioned elements.

{{InteractiveExample("CSS Demo: left")}}

```css interactive-example-choice
left: 0;
```

```css interactive-example-choice
left: 4em;
```

```css interactive-example-choice
left: 10%;
```

```css interactive-example-choice
left: 20px;
```

```html interactive-example
<section id="default-example">
  <div class="example-container">
    <div id="example-element">I am absolutely positioned.</div>
    <p>
      As much mud in the streets as if the waters had but newly retired from the
      face of the earth, and it would not be wonderful to meet a Megalosaurus,
      forty feet long or so, waddling like an elephantine lizard up Holborn
      Hill.
    </p>
  </div>
</section>
```

```css interactive-example
.example-container {
  border: 0.75em solid;
  padding: 0.75em;
  text-align: left;
  position: relative;
  width: 100%;
  min-height: 200px;
}

#example-element {
  background-color: #264653;
  border: 4px solid #ffb500;
  color: white;
  position: absolute;
  width: 140px;
  height: 60px;
}
```

## Syntax

```css
/* <length> values */
left: 3px;
left: 2.4em;
left: anchor(--myAnchor 50%);
left: calc(anchor-size(--myAnchor inline, 100px) * 2);

/* <percentage>s of the width of the containing block */
left: 10%;

/* Keyword value */
left: auto;

/* Global values */
left: inherit;
left: initial;
left: revert;
left: revert-layer;
left: unset;
```

### Values

- {{cssxref("&lt;length&gt;")}}
  - : A negative, null, or positive {{cssxref("&lt;length&gt;")}}:
    - for _absolutely positioned elements_, it represents the distance to the left edge of the containing block.
    - for _anchor-positioned elements_, the {{cssxref("anchor()")}} function resolves to a {{cssxref("&lt;length&gt;")}} value relative to the position of the associated _anchor element_'s left or right edge (see [Using inset properties with `anchor()` function values](/en-US/docs/Web/CSS/CSS_anchor_positioning/Using#using_inset_properties_with_anchor_function_values)), and the {{cssxref("anchor-size()")}} function resolves to a {{cssxref("&lt;length&gt;")}} value relative to the associated anchor element's width or height (see [Setting element position based on anchor size](/en-US/docs/Web/CSS/CSS_anchor_positioning/Using#setting_element_position_based_on_anchor_size)).
    - for _relatively positioned elements_, it represents the distance that the element is moved to the right of its normal position.

- {{cssxref("&lt;percentage&gt;")}}
  - : A {{cssxref("&lt;percentage&gt;")}} of the containing block's width.
- `auto`
  - : Specifies that:
    - for _absolutely positioned elements_, the position of the element is based on the {{Cssxref("right")}} property, while `width: auto` is treated as a width based on the content; or if `right` is also `auto`, the element is positioned where it should horizontally be positioned if it were a static element.
    - for _relatively positioned elements_, the distance of the element from its normal position is based on the {{Cssxref("right")}} property; or if `right` is also `auto`, the element is not moved horizontally at all.

## Description

The effect of `left` depends on how the element is positioned (i.e., the value of the {{cssxref("position")}} property):

- When `position` is set to `absolute` or `fixed`, the `left` property specifies the distance between the element's outer margin of left edge and the inner border of left edge of its containing block. (The containing block is the ancestor to which the element is relatively positioned.) If the positioned element has an associated [_anchor element_](/en-US/docs/Web/CSS/CSS_anchor_positioning/Using), and the property value includes an {{cssxref("anchor()")}} function, `left` positions the left edge of the positioned element relative to the position of the specified [`<anchor-side>`](/en-US/docs/Web/CSS/anchor#anchor-side) edge. The `left` property is [compatible](/en-US/docs/Web/CSS/anchor#compatibility_of_inset_properties_and_anchor-side_values) with the `left`, `right`, `start`, `end`, `self-start`, `self-end`, `center`, and `<percentage>` values.
- When `position` is set to `relative`, the `left` property specifies the distance the element's left edge is moved to the right from its normal position.
- When `position` is set to `sticky`, the `left` property is used to compute the sticky-constraint rectangle.
- When `position` is set to `static`, the `left` property has _no effect_.

When both `left` and {{cssxref("right")}} are defined, and width constraints don't prevent it, the element will stretch to satisfy both. If the element cannot stretch to satisfy both, the position of the element is _overspecified_. When this is the case, the `left` value has precedence when the container is left-to-right; the `right` value has precedence when the container is right-to-left.

## Formal definition

{{cssinfo}}

## Formal syntax

{{csssyntax}}

## Examples

### Positioning elements

#### HTML

```html
<div id="wrap">
  <div id="example_1">
    <pre>
      position: absolute;
      left: 20px;
      top: 20px;
    </pre>
    <p>
      The only containing element for this div is the main window, so it
      positions itself in relation to it.
    </p>
  </div>

  <div id="example_2">
    <pre>
      position: relative;
      top: 0;
      right: 0;
    </pre>
    <p>Relative position in relation to its siblings.</p>
  </div>

  <div id="example_3">
    <pre>
      float: right;
      position: relative;
      top: 20px;
      left: 20px;
    </pre>
    <p>Relative to its sibling div above, but removed from flow of content.</p>

    <div id="example_4">
      <pre>
        position: absolute;
        bottom: 10px;
        right: 20px;
      </pre>
      <p>Absolute position inside of a parent with relative position</p>
    </div>

    <div id="example_5">
      <pre>
        position: absolute;
        right: 0;
        left: 0;
        top: 200px;
      </pre>
      <p>Absolute position with both left and right declared</p>
    </div>
  </div>
</div>
```

#### CSS

```css
#wrap {
  width: 700px;
  margin: 0 auto;
  background: #5c5c5c;
}

pre {
  white-space: pre-line;
  word-wrap: break-word;
}

#example_1 {
  width: 200px;
  height: 200px;
  position: absolute;
  left: 20px;
  top: 20px;
  background-color: #d8f5ff;
}

#example_2 {
  width: 200px;
  height: 200px;
  position: relative;
  top: 0;
  right: 0;
  background-color: #c1ffdb;
}
#example_3 {
  width: 600px;
  height: 400px;
  position: relative;
  top: 20px;
  left: 20px;
  background-color: #ffd7c2;
}

#example_4 {
  width: 200px;
  height: 200px;
  position: absolute;
  bottom: 10px;
  right: 20px;
  background-color: #ffc7e4;
}
#example_5 {
  position: absolute;
  right: 0;
  left: 0;
  top: 100px;
  background-color: #d7ffc2;
}
```

#### Result

{{EmbedLiveSample('Positioning_elements',1200,650)}}

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{cssxref("top")}}, {{cssxref("bottom")}}, and {{cssxref("right")}}
- {{cssxref("inset")}} shorthand
- {{cssxref("inset-block-start")}}, {{cssxref("inset-block-end")}}, {{cssxref("inset-inline-start")}}, and {{cssxref("inset-inline-end")}}
- {{cssxref("inset-block")}} and {{cssxref("inset-inline")}} shorthands
- {{cssxref("position")}}
- [CSS positioned layout](/en-US/docs/Web/CSS/CSS_positioned_layout) module
