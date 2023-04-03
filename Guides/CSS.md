# CSS - Cascading Style Sheets

## Summary

1. [CSS Basics](#css-basics)
1. [CSS Selectors](#css-selectors)
1. [CSS Colors](#css-colors)
1. [CSS Units](#css-units)
1. [CSS Typograph](#css-typograph)
1. [CSS Box Model](#css-box-model)
1. [Shadows](#shadows)
1. [Background Images](#background-images)
1. [CSS Elements Positioning](#css-elements-positioning)
1. [Media Queries](#media-queries)
1. [Pseudo-Elements](#pseudo-elements)
1. [Pseudo-Classes](#pseudo-classes)
1. [Transform](#transform)
1. [Transitions](#transitions)
1. [Animations](#animations)
1. [CSS Variables](#css-variables)
1. [CSS Flexbox](#css-flexbox)
1. [CSS Grid](#css-grid)

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

## Cascading

Cascading Style means that parent elements will pass some of their style to their child elements. One example is that any elements of the page will inherit some of the styling of the HTML body element.

The child elements styling can still overwrite this.  
CSS property styling will always overwrite the old style of the same property.

---

# CSS Selectors

Selectors determines which elements will receive a rule.
The main ones are the following:

```css
element  /* this select all the elements of that type*/
.class    /* to select a class, use the dot before the name*/
#id       /* to select by id, use the number sign before the name*/
*         /* this is the universal selector, it selects everything*/
```

## To combine selectors:

Just put one selector after the other without space

```css
div.class-1.class-2#id-1 /*This will select divs that has class-1, class-2 and id-1*/
```

## Adding selections

You can combine multiple selectors:

```css
element1, element2, element3
```

## Select only direct children of an element

```css
div > h1  /* this would select only h1 that are direct child of a div */
div > .class
.container > p
```

## Select descendants of an element

```css
div h1  /* this would select all h1 that are descendants of divs */
div .class   /* this would select all descendants elements of div that have the class */
.container p /* would select all the paragraphs elements inside of elements have the container class */
```

---

# CSS Colors

```css
color: red; /* text and border colors */
background-color: black;
background: black; /* can be used as background-color or to insert an image as background */
```

## Colors definitions in CSS:

Predefined Color Names:

```css
color: red;
background: black;
```

RGB and RGBA values:

```css
color: rgb(0, 128, 255);
background: rgba(255, 200, 25, 0.5);
```

Hexadecimal Values with 3 ,4, 6 or 8 digits:

```css
color: #ff0000; /* 2 digits for each of the three color channels */
color: #f00; /* 1 digit for each of the three color channels */
background: #000000aa; /* 2 digits per color channels plus 2 for the alpha channel */
background: #000a; /* 1 digits per color channels plus 1 for the alpha channel */
```

HSL values:

```css
color: hsl(30, 80%, 50%);
```

Instead of using a unit, you can use the keyword auto in some places. Depending of the property, it will set it's value following a rule:

```css
height: auto;
```

---

# CSS Units

CSS units determines the size of the elements in the page.  
They can be used to set the height or width of elements, the font-size, the width of border, etc.  
The main ones are:

```css
pixels /* absolute value/unit*/
% /* relative value/unit. Depends on the parent (container) */

em /* relative value/unit. Depends on the parent (container) */
rem /* relative value/unit. Depends on the root (browser and html) */
/* 1em and 1rem = 16 px by default browser style */

vw /* view width percentage. 50vw means half of view width */
vh /* view height percentage. 50vh means half of view height */
```

## The calc function:

The calc function to make mixed units calculations.

```css
calc(100vh - 100px);
```

> Always put space between operations. `calc(100vh-100px)` wouldn't work!

---

# CSS Typograph

Typography:

```css
font-size
font-family: font_1, font_2, ..., font_n;
```

## Font generic families:

`serif, sans-serif, cursive, fantasy, monospace`

## Disclaimer about imported fonts:

Google Fonts links needs to be before the CSS links.  
Google Fonts import method should be placed before any styling rule.  
System fonts load faster than Google Fonts, but will look different in each system.

```css
font-weight /* a number that sets how thin of thick are the characters. It needs to a number that is supplied by the Fonts service. You can simply set it to keywords like normal, bold or lighter */
font-style /* italic, normal, oblique... */
text-align
text-indent /* units to indent the first row of the paragraph */
line-height /* if don't specify a unit, it will be based on the font size */
letter-spacing
word-spacing
text-transform /* controls the type of case */
text-decoration /* used to set things like underline, overline and line-through */
```

---

# CSS Box Model

Each element of the page is actually a box that hold the content, being that content other elements, text, images and other things.  
The dimension of each box is determined by the properties width and height:

```css
width: 500px;
height: 300px;
```

Minimum width and height by default are auto. this means that i will have the minumum width and height to envolve all of its contents. If you will change the default value, you can have problems with the container not envolving all of its contents. Fo fix this you can set a minimum and maximum width and heights:

```css
min_width: auto;
max-width: auto;
min_height: auto;
max_height: auto;
```

Each of the element's box, from outside to the inside has margins, outline, border, padding and the content.

```css
margin: 10px; /* determines the spacing between the elements */
padding: 10px; /* is the spacing between the border of the box and the contents */
```

> -   The margin of two adjacent elements don't add up. The margin of one will ocuppy the same space of the other's.
> -   So what determines the spacing between two elements, is the widest margin between the two.
> -   You can set the margin value to negative, so the elements of the page overlap or even swap positions.

For these last, set individual sizes or set multiple values for them:

```css
margin-top: 10px;
border-left: 3px solid black;
padding-bottom: 10px;

margin: 5px 10px; /* set the top and bottom margin to 5px, and the remaining to 10px */
margin: 5px 10px 3px 10px; /* set the top, right, bottom and left individualy*/

padding: 5px 10px;
padding: 5px 10px 3px 10px;
```

For the border we have multiple properties and a shorthand:

```css
border-width: 3px;
border-style: solid;
border-color: black;
border: 3px solid black; /* shorthand */
border-radius: 10px; /* sets the roundness of the box */
```

Outline is similar to border, but you can offset it using outline-offset.  
You can use border and outline at the same time.

```css
outline-width: 3px;
outline-style: solid;
outline-color: black;
outline: 3px solid black; /* shorthand */
outline-offset: 10px;
```

The box resizes to make space for the contents. If you don't want this behavior, you can hide the content that goes beyond this space, or even add a scrollbar to the box:

```css
overflow: hidden;
overflow: scroll;
```

## Display Property:

Block: always starts a new line a span all across the full page width.  
`<divs>`, `<headings>` and `<paragraphs>` have these by default.

```css
display: block;
```

Inline: does not starts a new line and doesn't span across the full page width.  
`<span>`, `<a>` and `<img>` have these by default.

Can be aligned horizontaly in the center by using text-align center on the its parent
The browser doesn't respect inline width, height and right and left margins

```css
display: inline;
```

Inline-block: a mix of the two. Doesn't start a new line, but the browser will respect the height and margins of the element.

None: it will remove the element from the document flow, hidding it.  
If you want to hide an element without removing it from the flow of the document, use the opacity or the visibility property.

## Box Sizing Property:

Determines how the padding will work.
With the default value, content-box, the padding will be done outside of the content box, so the padding will make the box increase size, but the content box will stay the same size.  
With the border-box value, the padding will be done inside the content box, so the padding won't make the element bigger but it will shink the content box.

```css
box-sizing: content-box; /* the content will stay the same size but the box increases */
box-sizing: border-box; /* the box will stay the same size but the content may shrink */
```

---

# Shadows

There are two main types of shadow in CSS:

Text Shadow:

```css
text-shadow: xpos ypos blur-amount color;
```

Box Shadow:

```css
box-shadow: xpos ypos blur-amount (spread) color;
```

---

# Background Images

The background property can be used to set a background color:

```css
background: url("image_path");
background: color url("image_path"); /* background color is for images with alpha */
background-repeat: repeat, no-repeat, repeat-x, repeat-y, space, round;
background-size: cover, contain;
background-position: center, top, right, bottom, left, x% y%;
background-attachment: fixed, scroll;
```

You can use a shorthand for these:

```css
background: color url("image_path") repeat attachment position;
```

Instead of a color or a image to background, you can set a linear-gradient.

```css
background: linear-gradient (optional_direction, color_1, color_2, ... color_n);
```

Instead of a color or a image to background, you can set a linear-gradient:
background: linear-gradient (optional_direction, color_1, color_2, ... color_n);
The optional_direction can be:

-   'to top'
-   'to right'
-   'to bottom'
-   'to left'
-   a mix of two directions (ex 'to top left')
-   Xdeg
    You can use percentages to expand the colors to make the gradient more tight:
    linear-gradient (blue 20%, yellow 50%)

You can mix images with linear overlay. Just separate them with a comma. Very useful to make an image overlay.  
In the following the transparent black gradient dims the images brightness.

```css
background: linear-gradient (rgba(0, 0, 0, 0.5), rgba(0, 0, 0, 0.5)), url("image_path");
```

## Object fit:

Object fit is used to decide how a image is going to be cropped. Good to scale images non-uniformly without distorting them.

```css
object-fit: cover;
object-fit: contain;
object-fit: fill;
object-fit: none;
object-fit: scale-down;
```

---

# CSS Elements Positioning

## The Float Property:

The float property is used for positioning and formatting content e.g. let an image float to the left of text in a container.

```css
img {
    float: right;
}
img {
    float: none;
}
```

To avoid a float behavior, you can use the clear property.

```css
div {
    clear: right;
}
```

## The Position Property:

You have five main ways of positioning the position of an element in the page, they are:

-   static: the default, always positioned according to the normal flow
-   relative: position the element relative to its own static position. You can shift the element using the properties top, right, left and bottom. Other content won't be adjusted to fill the gaps left by the shifted element.
-   absolute: relative to the closest parent with relative position. Place the element using the
    roperties top, right, left and bottom. Other content will be adjusted to fill the gaps left by the absolute element.
-   fixed: it will stay in the same screen position even if you scroll the screen, like a popup or a navbar that always stays at the top.
-   sticky: toogles between relative and fixed. Use the properties top, right, left and bottom to select the part the part of the screen the element will stick to.

```css
 {
    position: static;
    position: relative;
    position: absolute;
    position: fixed;
    position: sticky;
}
```

## Z-Index Property:

Z-index serves to determine what elements is draw in front or back. The default is 0. Bigger values will be draw in front and smaller in the back. You can set it to be negative too. Equal values means that the elements will be draw in top of other depending on their order in the HTML. It doesn't work with position static

```css
 {
    z-index: 1;
}
```

---

# Media Queries

Media queries apply their rules when certain conditions are met. They are useful to make the layout change for differents screens sizes, so an page will have different sizes on small screens (ie: phones), medium sized screens (ie: tablets) and big screens.

```css
@media screen and (min-width: 500px) {
    /* styling put here will be applied only if the screen width is 500 pixels or larger */
}
@media screen and (max-width: 500px) {
    /* styling put here will be applied only if the screen width is 500 pixels or smaller */
}
```

Media queries will overwrite anything that came before. A good rule to follow is start with smaller screens and then overwrite styling for medium and big screens. This way you can make the css load big background images only for big screens.

---

# Pseudo-Elements

A CSS pseudo-element is a keyword added to a selector that lets you style a specific part of the selected element(s).

## Before and After:

Each HTML element has pseudo-elements that are created automatically when the page is loaded. These elements come before and after the main element. By default they are empty, but you can use pseudo selectors can be used to edit them.

The "content" property is required.

```css
p::before {
    content: "Prefix message";
    color: red;
    display: block;
}
p::after {
    content: "Sufix message";
    color: blue;
    display: block;
}
```

Doesn't work with 'img' since these doesn't generate before and after pseudo-elements. To make it work put the image inside a 'div' and insert the pseudo-element in the div styling.

In place of using top, right, bottom, left, use 'inset' property as a short hand to them all.

```css
 {
    inset: 10px;
    inset: 10px 20px;
    inset: 10px 20px 10px 20px;
}
```

## First Line and First Letter:

```css
p::first-line {
}
p::first-letter {
}
```

---

# Pseudo-Classes

Pseudo-class are keywords added to a selector tha specifies a special state of the element.
Different from pseudo-elements, you use just one colon.

## Link pseudo-classes:

```css
a:link {
}
a:visited {
}
a:hover {
}
a:active {
}
```

## Root Pseudo-Class:

The root pseudo-class works the same way as the html selector, the only difference is that the root selector is more specific.  
The root is the perfect place to put all your global variables.

```css
html {
} /* less specific*/
:root {
} /* more specific*/
```

## Is Pseudo-Class Function:

The `:is()` CSS pseudo-class function takes a selector list as its argument, and selects any element that can be selected by one of the selectors in that list.

```css
/*only the h2 that are inside of nav, header or section*/
:is(nav, header, section) h2:hover {
    color: red;
}
/*only the h1, h2 or h3 that are inside of nav, header or section*/
:is(nav, header, section) :is(h1, h2, h3) {
    color: red;
}
```

## Not Pseudo-Class Function:

The `:not()` CSS pseudo-class function is the inverse of the `is` function.

```css
/* the following would select all elements with the class special that are not a h1 */
.special :not(h1) {
    color: red;
}
```

---

# Transform

Transform means an abrupt change of the positioning and shape of and element.

The transform consists of position, rotation, scale and deformation. You can change them with the following functions:

```css
div {
    transform: translate (x, y);
    transform: translateX (x);
    transform: translateY (y);

    transform: scale (factor);
    transform: scale (x, y);
    transform: scaleX (x);
    transform: scaleY (y);

    transform: rotate (deg);
    transform: rotateX (Xdeg);
    transform: rotateY (Ydeg);
    transform: rotateZ (Zdeg);

    transform: skew (Xdeg, Ydeg);
    transform: skew (Xdeg);
    transform: skewX (Xdeg);
    transform: skewY (Ydeg);
}
```

---

# Transitions

Transition is a change over time. It makes the transform changes less abrupt.

To make a transition, use the keyword 'transition-property' and set it to the name of the property that you want to make a transition. Then you would set the duration with the keyword 'transition-duration'.

As an example, for making a background-color transition you would declare inside the selector:

```css
/* when the user hovers over the div, the background color would have a nice transition to red color, then if the user stop hovering the cursor over it, the color would return back*/
div {
    transition-property: background-color;
    transition-duration: 1s;
}
div:hover {
    background-color: red;
}
```

To make multiple transitions, separate the transition-properties by comma, and if you want different duration values for each of them, just separate the duration with commas too.

```css
transition-property: background-color, border-radius;
transition-duration: 1s, 500ms;
```

If you want to delay the transition, use 'transition-delay' keyword and set it to a duration:

```css
transition-delay: 500ms;
```

## Transition Timing Functions:

Timing functions determines the acceleration of transitions and animations.

```css
ease
linear
ease-in
ease-out
ease-in-out
```

## Transition shorthand:

To set many transitions, you can use the keyword all to make the transition apply to all properties that change, or you can sperate transitions using commas.

```css
transition: all duration (transition-timing-function) (delay)
transition: property1 duration1 (transition-timing-function1) (delay1), property2...
```

---

# Animations

Animation is one or multiple changes over time, and with more control.

Before applying animation, keyframes are needed. To create keyframes for an animation use:

```css
@keyframes animation_name {
    0% {
        /* properties to be changed over time */
    }
    50% {
        /* properties to be changed over time */
    }
    100% {
        /* properties to be changed over time */
    }
}
```

> You 0% means the start of the animation, 100% the end, 50% the middle and so on...  
> You can use any number between 0% and 100% to set keyframes.  
> Inside each percentage/keyframe of the animation, put the all properties that you want to animate and the values of each keyframe.

To set the animation , use the properties:

```css
animation-name: animation_name;
animation-duration: 1s;
animation-iteration-count: 3; /* optional, how many times to play the animation, can be set to 'infinite'. The default is 1 */
```

## The Shorthand version:

```css
animation: name duration (iteration-count);
```

## Fill modes:

Determines what happens to the element properties after the animation is completed. Will it return to the original state or will continue with the values of the last frame of the animation?

```css
animation-fill-mode: backwards /* default, values are reseted after the animation is complete */
animation-fill-mode: forwards /* after the animation finishes, the values will stay the same as the last frame of the animation */
```

---

# CSS Variables

To declare reusable values use:

```css
--varName: value;
--primaryColor: #f15025;
--mainTransiiton: all 2s linear;
--mainSpacing: 5px;
```

To access it:

```css
property: var(--varName);
color: var(--primaryColor);
transition: var(--mainTransition);
letter-spacing: var(--mainSpacing);
```

You can have global variable or element local variables:

```css
:root {
    --global-color: red; /* declare in the root to make it global */
}
element {
    --local-color: red;
}
```

---

# CSS Flexbox

The CSS Flebox is an display value like 'in-line' or 'block'.
You can set the container display as 'flex' or 'inline-flex'.

```css
display: flex;
```

The parent container is refered as a "flex-container", and the children "flexitems".

-   Flex-Container = Parent Container.
-   Flex-Items = Childs of th Flex-Container.

A parent and children can be any HTML elements, as long it makes senses.

## Flex-Container Properties:

Flex-direction is the property that determines if the primary axis, the "Main Axis", will be vertical or horizontal. The secondary axis is called "Cross Axis".

```css
flex-direction: row;
flex-direction: row-reverse;
flex-direction: column;
flex-direction: column-reverse;
```

By default, the children will overflow the container, but you can make them wrap into new lines if the flex-container space isn't enough:

```css
flex-wrap: nowrap;
flex-wrap: wrap;
flex-wrap: wrap-reverse;
```

The justify property is responsible for the "Main Axis" alignment of the children:

```css
justify-content: flex-start;
justify-content: flex-end;
justify-content: center;
justify-content: space-between;
justify-content: space-around;
justify-content: space-evenly;
```

The align property is responsible for the "Cross Axis" alignment of the children. To make changes to this property visible, you need to assign a height value to the flex-container since by default it inherits the height of its children.

```css
align-items: stretch;
align-items: flex-start;
align-items: flex-end;
align-items: center;
align-items: baseline;
```

> ps: flex-start align the children to the top of the container, but baseline will align the children by the base of its contents.

A property similar to align-items, is align-content. The difference is that align-items each child a separated items, while align content treat the entire content as one thing.

```css
align-content: stretch;
align-content: flex-start;
align-content: flex-end;
align-content: center;
align-content: space-between;
align-content: space-around;
align-content: space-evenly;
```

You can add a gap space between the items:

```css
gap: 10px;
row-gap: 10px;
column-gap: 10px;
```

## Flex-Children Properties:

### Order:

You can change the order of an item. The default value is 0. Lower numbers come first. Elements with the same name will be ordered in the same flow as the html.

```css
order: 3;
```

### Align-Self:

Changes the alignment of just one item.

```css
align-self: stretch;
align-self: flex-start;
align-self: flex-end;
align-self: center;
align-self: baseline;
```

### Flex-Grow:

Determines if the child should grow to fill out the space left in the main axis. The value determines the proportion of the empty space each child will take.  
The default is `0`.

```css
flex-grow: 0;
```

### Flex-Shrink:

Determine if the child shoul shrink to adapt to the container size.  
The default is `1`.

```css
flex-shrink: 1;
```

### Flex-Basis

Determines the minimum width for the child. To avoid problems, it's recommended that the child has a display of border box and no left-right padding.  
The default is `auto`.

```css
flex-basis: auto;
```

### The Flex Shorthand:

You can use the short hand flex to set in one line the grow, shrink and basis.  
The default is `0 1 auto`.

```css
flex: grow shrink basis;
flex: 1 1 auto;
```

---

# CSS Grid

Grid is a display value used to setup two dimensional layouts.
Like Flexbox, the grid layout has a parent container and child items, called grid-container and grid-cells.

## Grid Container

```css
display: grid;
grid-template-columns: 200px 300px 200px; /* the width the each column, in this case is a 3 column grid */
```

While you don't setup the rows, you will have implicit grid. This means that CSS Grid will create more rows when it needs more space.

The auto keyword is a resposive wall determinimn the size of the column

```css
grid-template-columns: 25% 25% auto; /*the third columns will always occupy the remaining space of the container*/
grid-template-columns: auto auto auto; /*three columns of the same size*/
```

To set the number the number of rows manually, or explicit rows, use the property `grid-template-rows`.
If the number of items is bigger than the number of grid places, CSS Grid will create implicit rows.

```css
display: grid;
grid-template-columns: auto auto auto;
grid-template-rows: auto auto;
```

### Fr - Fraction Units

Fraction Units are used to break the grid space into columns and rows. 1fr means a fraction of available space.
It's easier than using percentages.

```css
grid-template-columns: auto auto auto;
grid-template-columns: 1fr 1fr 1fr;

grid-template-columns: 50% 50%;
grid-template-columns: 1fr 1fr;

grid-template-columns: 25% 50% 25%;
grid-template-columns: 1fr 2fr 1fr;
```

> Fraction Units works well with `grid-gap` property, while others units don't

### Gap

Like flexbox, we can use the gap property in Grid too.

```css
grid-row-gap: 1rem;
grid-column-gap: 2rem;
gap: 1rem 2rem; /* the frist value is the row gap */
gap: 1rem; /* applies for columns and rows */

grid-gap: 1rem 2rem; /* obsolete*/
grid-gap: 1rem; /* obsolete*/
```

## Grid Cells

Around and between the grid cells theres is a grid line, starting from 1 and going up.
A grid of 3 columns have would the 3 columns tracks where the cells would be sitting and around them 4 columns lines:

-   CL 1 - TRACK - CL 2 - TRACK - CL 3 - TRACK - CL 4

The same works for rows tracks and rows lines.

They should be referenced to control how the cells would occupy the grid space.

### Grid Column/Row Start/End

If you want a make a cell occupy more than 1 column of the grid, set the grid-columns-start and grid-columns-end:

```css
/* this styling sets the cell to use the all the column tracks between the column lines 1 and 3 */
grid-column-start: 1;
grid-column-end: 3;

grid-column: 1/3; /* short hand */
```

The same apply for rows:

```css
grid-row-start: 1;
grid-row-end: 3;

grid-row: 1/3; /* short hand */
```

It's possible to use negative numbers for start and end, -1 meaning the last line, -2 the line before it, and goes on.

```css
/* the following will make the cell ocupy the last column */
grid-column-start: -2;
grid-column-end: -1;

grid-column: -2/-1; /* short hand */
```

### Naming lines:

You can give names for lines and use them instead of numbers.
To name lines, at the grid-template-columns or grid-template-rows declaration, insert between the columns sizes a pair of square brackets with the desired name inside them.

```css
/* this example names the first and the last columns and row of the grid */
.grid-container {
    grid-template-columns: [start] 100px 100px 100px [end];
    grid-template-rows: [start] 100px 100px 100px [end];
}
/* then we set one of the cells to span all across the columns*/
.grid-cell-1 {
    grid-column: start/end;
}

/* another example */
.grid-container {
    grid-template-columns: [start] 100px 100px [middle] 100px 100px [end];
    grid-template-rows: [start] 100px 100px [middle] 100px 100px [end];
}
.grid-cell-1 {
    grid-column: start/middle;
}
.grid-cell-2 {
    grid-column: middle/end;
}
```

```css

```

```css

```

```css

```

```css

```

```css

```

```css

```
