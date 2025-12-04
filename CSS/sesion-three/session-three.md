Third session css

# CSS Tutorial - Session 3: Advanced Layouts & Responsive Design

## Agenda
- [Global Reset](#global-reset)
- [Overflow](#overflow)
- [Float](#float)
- [List Styling](#list-styling)
- [Opacity vs RGBA](#opacity-vs-rgba)
- [Multi-column Layout](#multi-column-layout)
- [Flexbox](#flexbox)
- [CSS Grid](#css-grid)
- [Transitions](#transitions)


----------------------------------------------------------------


- [Global Reset](#global-reset) 
Resets default browser styling and establishes a consistent box model.

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
``` 

---------------------------------------------------------------- 

- ## Overflow

  Controls content that exceeds container 
 
 ```css 

 .scroll-box { 
    height: 200px; 

    overflow: auto; /* visible | hidden | scroll */ 
    
 } 
 
 ``` 

 

---------------------------------------------------------------- 

 

- ## Float 

    Wraps content around elements 

 
```css 

  img { 

    float: left; 

    margin-right: 20px; 

  } 

``` 
 

---------------------------------------------------------------- 

 

- ## List Styling 

  Customizes list markers 

 

  ```css 

  ul { 

    list-style-position: inside; 

    list-style-type: square; 

  } 

``` 

 

---------------------------------------------------------------- 
---

- ## Opacity vs RGBA
  Controls element transparency.

  ```css
    .opacity-example{
      background: rgba(255,0,0,0.5); /* background only */
      opacity: 0.5 ; /* Entire element */

    }  
    
  ```

---
 
---------------------------------------------------------------- 

 

- ## Multi-column Layout 

  Creates newspaper-like layouts 

 

  ```css 

  .article { 

    column-count: 3; 

    column-gap: 40px; 

    column-rule: 2px solid #ddd; 

  } 

  ``` 

 

---------------------------------------------------------------- 

- ## Flexbox
  **Flexbox** creates flexible one-dimensional layouts that automatically adjust items to fit different screen sizes. It's ideal for navigation bars, cards, and any layout needing content alignment.

  ### Key Properties
  ```css
  .container {
    display: flex;
    justify-content: space-between; /* Horizontal alignment */
    align-items: center;     /* Vertical alignment */
    flex-wrap: wrap;        /* Allow items to wrap */
    gap: 20px;             /* Space between items */
  }

  .item {
    flex: 1 0 200px; /* flex-grow | flex-shrink | flex-basis */
    order: 2;        /* Change display order */
  }
  ```

  **Example**: Responsive navigation bar
  ```css
  .nav {
    display: flex;
    justify-content: space-around;
    padding: 1rem;
  }
 
  .nav-item {
    flex: 1;
    text-align: center;
  }
  ```

----------------------------------------------------------------

- ## CSS Grid
  **CSS Grid** creates complex two-dimensional layouts with rows and columns. Perfect for image galleries, dashboards, and magazine-style layouts.

  ### Core Concepts
  ```css
  .container {
    display: grid;
    grid-template-columns: repeat(3, 1fr); /* 3 equal columns */
    grid-template-rows: 100px auto;       /* Explicit row sizes */
    gap: 15px;                           /* Gutters */
  }

  .item {
    grid-column: 1 / span 2; /* Start at column 1, span 2 columns */
    grid-row: 2;            /* Place in second row */
    align-self: end;       /* Vertical positioning */
  }
  ```

  **Example**: Responsive gallery
  ```css
  .gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  }
  ```

----------------------------------------------------------------

- ## Transitions
  **Transitions** create smooth animations between state changes. Use them for hover effects, color changes, and size adjustments.

  ### Complete Syntax
  ```css
  .button {
    transition:
      background 0.3s ease-in-out,
      transform 0.2s linear 0.1s;
    /* property | duration | timing-function | delay */
  }
  ```

  **Example**: Smooth button hover
  ```css
  .btn {
    background: blue;
    transition: all 0.3s ease;
  }
 
  .btn:hover {
    background: darkblue;
    transform: translateY(-3px);
  }
  ```

----------------------------------------------------------------
