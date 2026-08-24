# Columns Block

## Overview

The Columns block lays out its single row of content in evenly distributed
columns (stacked on mobile, side-by-side from 900px up). A column whose only
content is a picture is automatically tagged as an image column so it can be
styled/ordered independently of text columns.

## Integration

### Block Configuration

This block does not read any `readBlockConfig()` keys. Content and column
count are derived directly from the authored table.

<!-- ### URL Parameters

No URL parameters affect this block's behavior. -->

<!-- ### Local Storage

No localStorage keys are used by this block. -->

<!-- ### Events

This block does not emit or listen to any custom events. -->

## Behavior Patterns

### Layout Behavior

- **Column count class**: the block adds `columns-<n>-cols` (n = number of
  columns in the first row) to the block element.
- **Image columns**: any column whose only child is a `<picture>` gets the
  `columns-img-col` class and is rendered full width; on mobile it is
  reordered before the text columns.
- **Responsive**: columns stack vertically below 900px and sit side-by-side
  (flex, centered) at 900px and above.

## Variants

### `hero-banner`

Author by setting the block name/options cell to `Columns (hero-banner)` ->
renders as `class="columns hero-banner"`.

Two-column homepage hero: the first column is styled as a white card
(logo image, `<h1>`, body copy, CTA link) that sits above the second column,
a full-bleed image. Intended to be placed inside a section whose Section
Metadata `Style` is set to `AHA Red` (see `styles/styles.css`) so the card
appears to float on the AHA-red brand background.

```
| Columns (hero-banner) | |
|------------------------|---|
| ![logo](...) \n # Heading \n Body copy \n [Shop Now](url) | ![hero image](...) |
```

### Error Handling

- **Uneven columns**: rows with a different number of columns than the
  first row still render; the `columns-<n>-cols` class reflects the first
  row's column count only.
- **No image column**: if no column contains a lone picture, all columns
  render as plain text columns.
