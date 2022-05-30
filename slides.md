---
theme: default
background: /cover-1.jpeg
highlighter: shiki
lineNumbers: false
fonts:
  sans: 'Inter'
  serif: 'Inter'
  mono: 'Inter'
  weights: '400,600'
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
drawings:
  persist: false
monaco: true
title: Academy - Advanced CSS
---

<style>
  ul { list-style: decimal; }
</style>

# Academy - Advanced CSS

Deep dive into the fundamentals of CSS.

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---

# Here we will cover:

- **Layout Modes** - Flow, Table, Positioned, Flex, CSS Grid
- **Positioning** - static, relative, absolute, fixed, sticky
- **Overflow** - hidden, auto, scroll
- **Layering** - Static Layer, Relative, Absolute, z-index
- **Selectors** - div, span, .className, #id, ::first-child etc
- **Transform & Transitions** - Origin, 2D, 3D, Scale, Translate, Rotate, Skew
- **Animations** - duration, easing-function, delay, iteration-count, direction, fill-mode, play-state, name
- **At-rules** - @media, @keyframe, @supports, 
- **CSS Variables** - var(--variable)
- **Colours** - HEX, RGB, HSL, Shadows, Gradients

<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/guide/syntax#embedded-styles
-->

---
layout: two-cols
---
# Layout Modes

The core of UI design with CSS are layouts. Layouts come in all shapes and sizes. A layout designed for a desktop is dramatically different to a mobile phone layout.

All of these layouts are created with CSS Layout modes.

- Flow
- Table
- Float
- Positioned
- Flex - Flexible Box
- CSS Grid

::right::

<style>
img {
  position: relative;
  z-index: 10;
  margin-top: -1.5rem;
}
</style>

![Layout Modes](/css-layout-mode.png)

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
layout: section
---

# Flow

---

# Default Flow

Since the first browser was first created in the 1990, the normal layout mode is called Flow. This is very similar to word documents. It stacks blocks on top of each other, and lays basic elements out horizontally next to each other.

The two main CSS properties for Flow are `display block` and `display inline`

---
layout: two-cols
class: center-column
---

## Example of Flow

Below we have a two div elements that have a width and height of 50px.

With a little margin you can see that the Flow layout stacks these elements on top of each other.

```html {monaco}
<style>
.box {
  margin: 50px;
  width: 150px;
  height: 150px;
  background: #fff;
  display: block;
}
</style>
<div class="box">Box 1</div>
<div class="box">Box 2</div>
```

::right::

<CodeSnippet :html="`<div> test </div>`" css="123" />

<!-- 
- Divs stack by default because of display:block.
- Margin is collapses in Flow Mode

- Changing block to display:inline
-->

---
layout: two-cols
---

<style>
.two-columns {
  @apply gap-10
}

.two-columns img[src*="7rem"] {
  height: 7rem;
  margin-bottom: 3rem;
  display: block;
}
</style>

![Display Block](/block.png#7rem)
### Block elements

- Block elements respect width and height
- Margin top, right, bottom, left apply to blocks
- Block elements have 100% width by default
  - E.g A `<P>` tag will fill the horizontal space
- Blocks take up the vertical space they need

::right::

![Display Block](/inline.png#7rem)
### Inline elements

- Inline elements ignore width and height
  - This is because inline elements flow with content on the page.
- Margin top and bottom are also ignored
- Inline only take up the space they need


---
layout: section
---

# Table

---
layout: default
---

# Table Layout

Tables are for structured data in rows and columns and when they work very well with accessibility tools such as screen readers which help with sighted and visually impaired users.

## Usecases
- Structured Data
- Numerical Data
- Accessable

## Potental Issues
- Responsive Design
- Desktop First / Not usable on mobiles


---
layout: section
---

# Float
---
layout: default
---
# Float Layout

TODO

---
layout: section
---

# Positioned
---
layout: default
--- 

# Positioned

TODO

---
layout: section
---

# Flex / Flexbox
---
layout: default
--- 

# Flex

TODO

---
layout: section
---

# CSS Grid
---
layout: default
--- 

# CSS Grid

TODO

```html {monaco}
<style>
.grid {
	grid-template-columns: repeat(2, 1fr);
	display: grid;
}
</style>
<div class="grid">
  <div style="background: red"></div>
  <div style="background: blue"></div>
  <div style="background: red"></div>
  <div style="background: blue"></div>
  <div style="background: red"></div>
</div>
```


