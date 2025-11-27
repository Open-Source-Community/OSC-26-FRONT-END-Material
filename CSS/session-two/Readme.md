# CSS Tutorial - Session 2: Core Styling

## Agenda

- [Border](https://github.com/nadamedhat27/Full-Stack/tree/main/Front-End/CSS#border)
- [Outline](https://github.com/nadamedhat27/Full-Stack/tree/main/Front-End/CSS#outline)
- [Display](https://github.com/nadamedhat27/Full-Stack/tree/main/Front-End/CSS#display)
- [Global Reset](#global-reset)
- [Text Styling](#text-styling)
- [Shadows](#shadows)
- [Transforms](#transforms)
- [Pseudo-classes](#pseudo-classes)
- [Background Gradients](#background-gradients)

---

- ## Border
  Same as the padding and margin property, all things explained there can be applied here, and it's written like this:

  ```css
  div {
    border-width: 10px;
    /*
      Same as:
      border-top-width: 10px;
      border-right-width: 10px;
      border-bottom-width: 10px;
      border-left-width: 10px;
    */
  }
  ```
  But here we can specify the border color like this:
  ```css
  div {
    border-color: red;
    /*
      Same as:
      border-top-color: red;
      border-right-color: red;
      border-bottom-color: red;
      border-left-color: red;
    */
  }
  ```
  And we can specify the border style like this:
  ```css
  div {
    border-style: solid;
    /*
      Same as:
      border-top-style: solid;
      border-right-style: solid;
      border-bottom-style: solid;
      border-left-style: solid;
    */
  }
  ```
  We can change the border sharpness by `border-radius` like this:
  ```css
  div {
    border-radius: 5px;
    /*
      Same as:
      border-top-radius: 5px;
      border-right-radius: 5px;
      border-bottom-radius: 5px;
      border-left-radius: 5px;
    */
  }
  ```
  Last thing we can specify the border width, style, and color by a shorthand statement like this:
  ```css
  div {
    border: 10px solid red;
  }
  ```

----------------------------------------------------------------

- ## Outline
  This property is used to add a border same as `border` property but with some differences. It's written like this:
  ```css 
  div {
    outline: 10px solid red;
    /*
      Same as:
      outline-width: 10px;
      outline-style: solid;
      outline-color: red;
    */
  }
  ```
  So, it means *No Sides* like `outline-right` or `outline-left`. The other difference is that the border size is taken from the element but the outline is not like that, it takes size from outside the element.

----------------------------------------------------------------

- ## Display
  It's responsible for the way of displaying the element, there are 3 different values this property can have: `block`, `inline-block`, and `inline`.
  
  1. **Block:** 
      - The width of the element is set to the full page width by default (if we didn't specify the width).
      - Adds line breaks before and after the element.
      - We can specify the padding, margin, width, and height of the element or any other property.
  2. **Inline:**
      - We can't specify the width or the height of the element.
      - Doesn't add line breaks before and after the element.
      - We can specify the padding, and margin but only the left and right sides are respected not the top or bottom sides.
      - Elements are side to side.
  3. **Inline-Block:** It's a mix of the inline and the block.
      - Doesn't add line breaks before and after the element.
      - We can specify the padding, margin, width, and height of the element or any other property.
      - Elements are side to side.
  ```css
  span {
    display: inline-block;
    /*
      Other Examples:

      -> display: inline;
      -> display: block;
    */
  }
  ```

----------------------------------------------------------------

- ## Element Visibility and Use Cases
  We can use `display` and `Visibility` properties for managing the Visibility of the element. 

  The difference between them is:
  
  1. `display`:
   
      ```css
      div {
        display: none;
      }
      ```
      The element is completely gone from the page, and also the no space for it, **like: dropdown lists**
  2.  `Visibility`: 
      ```css 
      div {
        visibility: hidden;
      }
      ```
      The element is only hidden but it's space still exists.


## Global Reset

Resets default browser styling and establishes a consistent box model.

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
```

---

## Text Styling

### Text Alignment
Controls horizontal text positioning.

```css
.center { text-align: center; }
.justify { text-align: justify; }
```

### Text Decoration
Adds lines/effects to text.

```css
.underline {
    text-decoration: underline wavy red 2px; /* line | style | color | thickness */
}
```

### Text Transform
Changes text capitalization.

```css
.upper { text-transform: uppercase; }
.capital { text-transform: capitalize; }
```

### Text Spacing
Controls text layout and spacing.

```css
p {
    text-indent: 40px;
    letter-spacing: 1px;
    word-spacing: 3px;
    line-height: 1.6;
}
```

### Text Shadow
Adds depth to text elements.

```css
h1 {
    text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.5); /* X | Y | Blur | Color */
}
```

-----------------------------------------------------------------

## Shadows

Creates depth effects for elements.

```css
.card {
    box-shadow: 5px 5px 15px 2px rgba(0, 0, 0, 0.3); /* X | Y | Blur | Spread | Color */
}
```

----------------------------------------------------------------------------------

## Transforms

Modifies an element's shape or position.

```css
.button {
    transform: scale(1.1) rotate(5deg);
    transition: transform 0.3s ease;
}
```

--------------------------------------------------------------------------

## Pseudo-classes

Styles elements based on state.

```css
a:hover { color: #ff4757; }
button:active { transform: scale(0.95); }
input:focus { outline: 2px solid #2ed573; }
.clickable { cursor: pointer; }
```

-----------------------------------------------------------------

## Background Gradients

Creates color transitions.

### Linear Gradient

```css
.header {
    background: linear-gradient(45deg, #ff6b6b, #4ecdc4);
}
```

### Radial Gradient

```css
.circle {
    background: radial-gradient(circle, #ff9a9e, #fad0c4);
}
```

--------------------------------------------------------------------


