# CSS - Cascading Style Sheets

## Summary

1. [CSS Basics](#css-basics)

---

# CSS Basics

## Basic CSS syntax

The basic syntax for an CSS rule is the following:

```css
selector {
    property: value;
}
```

## Inline CSS

To include inline CSS, just use the `style` attribute inside the HTML tag

```html
<p style="color:red; font-weight:bold">This is a red colored bold paragraph</p>
```

## Internal CSS

To include internal CSS, use the `<style></style>` tag inside the head of your HTML and put the your rules inside

## External CSS

To include external CSS, just use a `<link>` element in the HTML head:

```html
<link rel="stylesheet" href="file_name" />
```

CSS property styling will always overwrite the old style of the same property.
