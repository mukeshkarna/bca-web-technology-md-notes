# CSS: Student Notes

## Cascading Style Sheets (CSS)

### Definition and Introduction

CSS (Cascading Style Sheets) is a stylesheet language used to describe the presentation of a document written in HTML. CSS describes how elements should be rendered on screen, on paper, in speech, or on other media.

### Importance of CSS

CSS is crucial in web development because it:

1. **Separates content from presentation**
   - HTML provides structure and content
   - CSS controls how that content looks

2. **Improves site maintenance**
   - Change the look of an entire website by modifying a single file
   - Consistent styling across multiple pages

3. **Enhances user experience**
   - Better control over layout and design
   - Supports responsive design for different devices

4. **Reduces page load time**
   - Smaller file sizes compared to using presentational HTML
   - CSS can be cached by browsers

5. **Provides advanced styling capabilities**
   - Animations and transitions
   - Complex layouts
   - Visual effects

### Different Approaches to Style Sheets

There are three primary methods to include CSS in an HTML document:

#### 1. Inline CSS

CSS applied directly to HTML elements using the `style` attribute:

```html
<p style="color: red; font-size: 16px;">This is a paragraph with inline styles.</p>
```

**Advantages:**
- Immediately applies to the specific element
- No additional files needed
- Useful for quick, element-specific styling

**Disadvantages:**
- Mixes content with presentation
- Cannot be reused
- Higher maintenance effort for consistent styling
- Overrides other CSS methods (may complicate debugging)

#### 2. Internal CSS (Embedded)

CSS placed within a `<style>` element in the document's `<head>` section:

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        p {
            color: blue;
            font-size: 14px;
        }
        .highlight {
            background-color: yellow;
        }
    </style>
</head>
<body>
    <p>This is a blue paragraph.</p>
    <p class="highlight">This is a highlighted paragraph.</p>
</body>
</html>
```

**Advantages:**
- Applies to all matching elements in the page
- No additional files to download
- Classes and IDs can be reused within the page

**Disadvantages:**
- Only applies to the current page
- Increases page size
- Cannot be cached for use across multiple pages

#### 3. External CSS

CSS stored in a separate file (.css extension) and linked to HTML documents:

```html
<!DOCTYPE html>
<html>
<head>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <p>This paragraph is styled by the external CSS file.</p>
    <div class="container">This div is also styled externally.</div>
</body>
</html>
```

Contents of `styles.css`:
```css
p {
    color: green;
    font-size: 16px;
}
.container {
    width: 80%;
    margin: 0 auto;
    padding: 20px;
    background-color: #f0f0f0;
}
```

**Advantages:**
- Separates HTML from CSS completely
- Can be used across multiple pages
- Browsers can cache the CSS file
- Easier maintenance for large sites
- Reduced file size for HTML documents

**Disadvantages:**
- Additional HTTP request to fetch the CSS file
- May cause brief unstyled content during page load

### Using Multiple Approaches

You can combine different CSS approaches in the same document. When styles conflict, CSS follows the "cascade" order of precedence:

1. Inline styles (highest priority)
2. Internal/External styles (priority based on order and specificity)
3. Browser default styles (lowest priority)

Example of combined approaches:

```html
<!DOCTYPE html>
<html>
<head>
    <!-- External CSS -->
    <link rel="stylesheet" href="styles.css">
    
    <!-- Internal CSS -->
    <style>
        p {
            color: blue;
            font-size: 18px;
        }
    </style>
</head>
<body>
    <!-- Inline CSS -->
    <p style="color: red;">This will be red text (inline overrides internal and external)</p>
    
    <p>This will be blue text (internal CSS)</p>
</body>
</html>
```

### Linking to Style Information in Separate File

To link an external CSS file, use the `<link>` element in the document's `<head>` section:

```html
<head>
    <link rel="stylesheet" type="text/css" href="styles.css">
</head>
```

Attributes of the `<link>` element:
- `rel="stylesheet"`: Defines the relationship as a stylesheet
- `type="text/css"`: Specifies the MIME type (optional in HTML5)
- `href="styles.css"`: Path to the CSS file
- `media="screen"`: Optional attribute to specify which media type the styles apply to

You can link multiple stylesheets:

```html
<head>
    <link rel="stylesheet" href="base.css">
    <link rel="stylesheet" href="layout.css">
    <link rel="stylesheet" href="colors.css">
</head>
```

### Setting up Style Information

#### CSS Syntax

CSS consists of selectors and declarations:

```css
selector {
    property: value;
    another-property: value;
}
```

- **Selector**: Targets HTML elements to style
- **Property**: The style attribute you want to change
- **Value**: The setting for the property

Example:
```css
h1 {
    color: navy;
    font-size: 24px;
    text-align: center;
}
```

#### CSS Selectors

1. **Element Selector**
   ```css
   p {
       color: blue;
   }
   ```

2. **Class Selector**
   ```css
   .highlight {
       background-color: yellow;
   }
   ```

3. **ID Selector**
   ```css
   #header {
       background-color: black;
       color: white;
   }
   ```

4. **Descendant Selector**
   ```css
   article p {
       font-style: italic;
   }
   ```

5. **Child Selector**
   ```css
   ul > li {
       list-style-type: square;
   }
   ```

6. **Attribute Selector**
   ```css
   input[type="text"] {
       border: 1px solid gray;
   }
   ```

7. **Pseudo-class Selector**
   ```css
   a:hover {
       text-decoration: none;
   }
   ```

8. **Pseudo-element Selector**
   ```css
   p::first-line {
       font-weight: bold;
   }
   ```

### Using the `<LINK>` Tag

The `<link>` tag is placed in the document's `<head>` section to connect an HTML document to external resources, most commonly CSS files.

Basic syntax:
```html
<link rel="stylesheet" href="path/to/stylesheet.css">
```

Additional attributes:
- `media`: Specifies what device/media the linked document is optimized for
  ```html
  <link rel="stylesheet" href="print.css" media="print">
  <link rel="stylesheet" href="mobile.css" media="screen and (max-width: 600px)">
  ```
  
- `integrity`: Contains inline metadata used for subresource integrity checking
  ```html
  <link rel="stylesheet" href="https://cdn.example.com/styles.css" 
        integrity="sha384-oqVuAfXRKap7fdgcCY5uykM6+R9GqQ8K/uxy9rx7HNQlGYl1kPzQho1wx4JwY8wC" 
        crossorigin="anonymous">
  ```

- `crossorigin`: Indicates whether the resource should be fetched with CORS
  ```html
  <link rel="stylesheet" href="https://example.com/styles.css" crossorigin="anonymous">
  ```

### Embedded Style Information

Embedded styles (also called internal styles) are defined in the `<style>` element within the document's `<head>` section.

#### Using `<STYLE>` Tag

```html
<head>
    <style type="text/css">
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 20px;
            background-color: #f0f0f0;
        }
        
        h1 {
            color: #333;
            border-bottom: 2px solid #999;
        }
        
        .container {
            width: 80%;
            margin: 0 auto;
            padding: 15px;
            background-color: white;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
        }
    </style>
</head>
```

Attributes for the `<style>` tag:
- `type="text/css"`: Specifies the MIME type (optional in HTML5)
- `media="screen"`: Optional attribute to specify which media type the styles apply to

### Inline Style Information

Inline styles apply to individual HTML elements using the `style` attribute.

#### Using Style Attribute

```html
<p style="color: blue; font-size: 16px; margin-left: 20px;">
    This paragraph has inline styles.
</p>

<div style="background-color: #e0e0e0; padding: 15px; border: 1px solid #999;">
    This div also has inline styles.
</div>
```

### CSS1/2/3 Implementation

CSS has evolved through several versions, each adding new features:

#### CSS1 (1996)

Basic styling capabilities:
- Font properties
- Text properties
- Color and background
- Margins, borders, padding
- Basic positioning

```css
/* CSS1 Example */
p {
    font-family: Arial;
    color: blue;
    background-color: #f0f0f0;
    margin: 10px;
    padding: 5px;
    border: 1px solid black;
}
```

#### CSS2 (1998) and CSS2.1 (2011)

Extended features:
- Z-index
- Media types
- Bidirectional text
- Absolute, relative, and fixed positioning
- More sophisticated selectors

```css
/* CSS2 Example */
@media print {
    body {
        font-size: 12pt;
        color: black;
    }
}

div {
    position: absolute;
    top: 50px;
    left: 100px;
    z-index: 5;
}
```

#### CSS3 (Modular Specifications)

CSS3 was divided into smaller modules that could evolve independently:

1. **Selectors**
   ```css
   /* Child selector */
   ul > li {
       color: blue;
   }
   
   /* Attribute selectors */
   input[type="text"] {
       border: 1px solid gray;
   }
   
   /* Pseudo-classes */
   li:nth-child(odd) {
       background-color: #f0f0f0;
   }
   ```

2. **Box Model**
   ```css
   .container {
       box-sizing: border-box;
       box-shadow: 0 0 10px rgba(0,0,0,0.5);
   }
   ```

3. **Backgrounds and Borders**
   ```css
   .rounded-box {
       border-radius: 10px;
       background-image: linear-gradient(to bottom, #fff, #e0e0e0);
       border: 1px solid #999;
   }
   ```

4. **Text Effects**
   ```css
   h1 {
       text-shadow: 2px 2px 5px rgba(0,0,0,0.3);
       text-overflow: ellipsis;
       overflow: hidden;
       white-space: nowrap;
   }
   ```

5. **2D/3D Transformations**
   ```css
   .rotate {
       transform: rotate(45deg);
   }
   
   .cube {
       transform: perspective(500px) rotateY(45deg);
   }
   ```

6. **Animations and Transitions**
   ```css
   /* Transition */
   button {
       background-color: blue;
       transition: background-color 0.3s ease;
   }
   
   button:hover {
       background-color: darkblue;
   }
   
   /* Animation */
   @keyframes slide-in {
       from { transform: translateX(-100%); }
       to { transform: translateX(0); }
   }
   
   .animated {
       animation: slide-in 1s ease forwards;
   }
   ```

7. **Multiple Column Layout**
   ```css
   .content {
       column-count: 3;
       column-gap: 20px;
       column-rule: 1px solid #ccc;
   }
   ```

8. **Flexbox**
   ```css
   .container {
       display: flex;
       justify-content: space-between;
       align-items: center;
       flex-wrap: wrap;
   }
   
   .item {
       flex: 1 1 200px;
       margin: 10px;
   }
   ```

9. **Grid Layout**
   ```css
   .grid {
       display: grid;
       grid-template-columns: repeat(3, 1fr);
       grid-gap: 20px;
   }
   
   .header {
       grid-column: 1 / -1;
   }
   ```

10. **Media Queries**
    ```css
    @media screen and (max-width: 600px) {
        .container {
            flex-direction: column;
        }
        
        body {
            font-size: 14px;
        }
    }
    ```

### CSS Positioning

Positioning allows you to control the layout of elements on the page.

#### Types of Positioning

1. **Static Positioning**
   - Default positioning
   - Elements follow normal document flow
   - `top`, `right`, `bottom`, `left` properties have no effect

   ```css
   .element {
       position: static;
   }
   ```

2. **Relative Positioning**
   - Positioned relative to its normal position
   - Other elements are not affected
   - Creates a positioning context for absolute children

   ```css
   .element {
       position: relative;
       top: 10px;
       left: 20px;
   }
   ```

3. **Absolute Positioning**
   - Positioned relative to nearest positioned ancestor (or the document body)
   - Removed from normal document flow
   - Other elements act as if it's not there

   ```css
   .element {
       position: absolute;
       top: 50px;
       left: 100px;
       width: 200px;
       height: 100px;
   }
   ```

4. **Fixed Positioning**
   - Positioned relative to the viewport
   - Stays in place during scrolling
   - Removed from normal document flow

   ```css
   .navbar {
       position: fixed;
       top: 0;
       left: 0;
       width: 100%;
       background-color: white;
       z-index: 100;
   }
   ```

5. **Sticky Positioning**
   - Hybrid between relative and fixed
   - Acts like relative positioning until it crosses a specified threshold
   - Then acts like fixed positioning

   ```css
   .section-header {
       position: sticky;
       top: 0;
       background-color: #f0f0f0;
       padding: 10px;
   }
   ```

#### Z-Index

The `z-index` property controls the stacking order of positioned elements:

```css
.background {
    position: absolute;
    z-index: 1;
}

.foreground {
    position: absolute;
    z-index: 2; /* Will appear on top of .background */
}
```

- Higher z-index values appear in front of elements with lower values
- Only works on positioned elements (not `position: static`)
- Creates stacking contexts

### CSS Box Model

The CSS box model describes the rectangular boxes generated for elements in the document tree.

#### Components of the Box Model

1. **Content**: The actual content of the element (text, images, etc.)
2. **Padding**: Space between the content and the border
3. **Border**: Line around the padding (if specified)
4. **Margin**: Space outside the border

```css
.box {
    /* Content dimensions */
    width: 300px;
    height: 200px;
    
    /* Padding */
    padding-top: 20px;
    padding-right: 15px;
    padding-bottom: 20px;
    padding-left: 15px;
    /* Shorthand: padding: 20px 15px 20px 15px; */
    /* Shorthand: padding: 20px 15px; (top/bottom, left/right) */
    
    /* Border */
    border-width: 2px;
    border-style: solid;
    border-color: #333;
    /* Shorthand: border: 2px solid #333; */
    
    /* Margin */
    margin-top: 10px;
    margin-right: 5px;
    margin-bottom: 10px;
    margin-left: 5px;
    /* Shorthand: margin: 10px 5px 10px 5px; */
    /* Shorthand: margin: 10px 5px; (top/bottom, left/right) */
}
```

#### Box Sizing

By default, the `width` and `height` properties only apply to the content box. The `box-sizing` property can change this behavior:

```css
/* Default box sizing (content-box) */
.content-box {
    box-sizing: content-box;
    width: 300px; /* Just the content width */
    padding: 20px;
    border: 2px solid black;
    /* Total width: 300px + 40px (padding) + 4px (border) = 344px */
}

/* Border box sizing */
.border-box {
    box-sizing: border-box;
    width: 300px; /* Total width including padding and border */
    padding: 20px;
    border: 2px solid black;
    /* Content width: 300px - 40px (padding) - 4px (border) = 256px */
}
```

Many developers apply border-box sizing to all elements for more intuitive sizing:

```css
* {
    box-sizing: border-box;
}
```

### CSS3 Specifics

#### Responsive Design with Media Queries

Media queries allow you to apply different styles based on device characteristics:

```css
/* Base styles for all devices */
body {
    font-size: 16px;
    padding: 20px;
}

/* Styles for small screens (mobiles) */
@media (max-width: 600px) {
    body {
        font-size: 14px;
        padding: 10px;
    }
    
    .container {
        width: 100%;
    }
}

/* Styles for medium screens (tablets) */
@media (min-width: 601px) and (max-width: 1024px) {
    .container {
        width: 90%;
    }
}

/* Styles for large screens */
@media (min-width: 1025px) {
    .container {
        width: 80%;
        max-width: 1200px;
    }
}

/* Print styles */
@media print {
    body {
        font-size: 12pt;
        color: black;
    }
    
    .no-print {
        display: none;
    }
}
```

#### Flexbox Layout

Flexbox is a one-dimensional layout method designed for laying out items in rows or columns:

```css
.container {
    display: flex;
    flex-direction: row; /* or column, row-reverse, column-reverse */
    flex-wrap: wrap; /* or nowrap, wrap-reverse */
    justify-content: space-between; /* main axis alignment */
    align-items: center; /* cross axis alignment */
    gap: 20px; /* spacing between items */
}

.item {
    flex: 1; /* grow, shrink, basis shorthand */
    /* flex: grow shrink basis; */
    /* e.g., flex: 1 0 200px; */
}

/* Target specific flex items */
.item:nth-child(1) {
    flex-grow: 2; /* takes twice as much space */
    align-self: flex-start; /* individual alignment */
    order: 2; /* change visual order */
}
```

#### Grid Layout

CSS Grid is a two-dimensional layout system designed for complex layouts:

```css
.grid-container {
    display: grid;
    grid-template-columns: repeat(3, 1fr); /* 3 equal columns */
    grid-template-rows: auto 200px auto; /* row heights */
    grid-gap: 20px; /* spacing between cells */
    /* or separately: */
    /* grid-column-gap: 20px; */
    /* grid-row-gap: 10px; */
}

.header {
    grid-column: 1 / -1; /* span all columns */
    /* or: grid-column: 1 / span 3; */
}

.sidebar {
    grid-row: 2 / 4; /* from row 2 to row 4 */
}

.content {
    grid-column: 2 / 4; /* from column 2 to column 4 */
    grid-row: 2; /* row 2 */
}

.footer {
    grid-column: 1 / -1; /* span all columns */
    grid-row: 4; /* row 4 */
}

/* Named grid areas */
.named-grid {
    display: grid;
    grid-template-columns: 200px 1fr 1fr;
    grid-template-rows: auto 1fr auto;
    grid-template-areas:
        "header header header"
        "sidebar content content"
        "footer footer footer";
}

.header { grid-area: header; }
.sidebar { grid-area: sidebar; }
.content { grid-area: content; }
.footer { grid-area: footer; }
```

#### Transitions and Animations

CSS transitions allow you to change property values smoothly over a specified duration:

```css
.button {
    background-color: blue;
    color: white;
    padding: 10px 20px;
    transition-property: background-color, transform;
    transition-duration: 0.3s, 0.2s;
    transition-timing-function: ease-out, ease-in;
    transition-delay: 0s, 0.1s;
    /* Shorthand: */
    /* transition: background-color 0.3s ease-out, transform 0.2s ease-in 0.1s; */
}

.button:hover {
    background-color: darkblue;
    transform: scale(1.05);
}
```

CSS animations allow you to create more complex animations with keyframes:

```css
@keyframes slide-in {
    0% {
        transform: translateX(-100%);
        opacity: 0;
    }
    60% {
        transform: translateX(10%);
    }
    100% {
        transform: translateX(0);
        opacity: 1;
    }
}

.animated-element {
    animation-name: slide-in;
    animation-duration: 1s;
    animation-timing-function: ease-out;
    animation-delay: 0.2s;
    animation-iteration-count: 1; /* or infinite */
    animation-direction: normal; /* or reverse, alternate, alternate-reverse */
    animation-fill-mode: forwards; /* or backwards, both, none */
    /* Shorthand: */
    /* animation: slide-in 1s ease-out 0.2s 1 normal forwards; */
}

/* Multiple animations */
.multi-animated {
    animation: 
        slide-in 1s ease-out forwards,
        fade 2s ease-in infinite alternate;
}
```

### Introduction to HTML5 and CSS3 Integration

HTML5 and CSS3 work together to create modern, feature-rich websites. Here are some common integrations:

#### Semantic HTML5 Elements with CSS3 Styling

```html
<!DOCTYPE html>
<html>
<head>
    <style>
        header {
            background: linear-gradient(to bottom, #3498db, #2980b9);
            color: white;
            padding: 20px;
            border-radius: 8px 8px 0 0;
        }
        
        nav {
            display: flex;
            background-color: #34495e;
            padding: 10px;
        }
        
        nav a {
            color: white;
            padding: 10px 15px;
            text-decoration: none;
            transition: background-color 0.3s;
        }
        
        nav a:hover {
            background-color: #2c3e50;
            border-radius: 4px;
        }
        
        section {
            padding: 20px;
            margin: 20px 0;
            border-left: 4px solid #3498db;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        
        article {
            margin-bottom: 20px;
            padding: 15px;
            background-color: #f9f9f9;
            border-radius: 4px;
        }
        
        footer {
            background-color: #34495e;
            color: white;
            text-align: center;
            padding: 20px;
            border-radius: 0 0 8px 8px;
        }
    </style>
</head>
<body>
    <header>
        <h1>My Website</h1>
    </header>
    
    <nav>
        <a href="#">Home</a>
        <a href="#">About</a>
        <a href="#">Services</a>
        <a href="#">Contact</a>
    </nav>
    
    <section>
        <h2>Main Content</h2>
        <article>
            <h3>Article Title</h3>
            <p>Article content goes here...</p>
        </article>
        <article>
            <h3>Another Article</h3>
            <p>More content here...</p>
        </article>
    </section>
    
    <footer>
        <p>&copy; 2025 My Website</p>
    </footer>
</body>
</html>
```

#### Responsive Web Design

```html
<!DOCTYPE html>
<html>
<head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        * {
            box-sizing: border-box;
        }
        
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
        }
        
        .container {
            width: 100%;
            padding: 0 15px;
            margin: 0 auto;
        }
        
        header {
            background-color: #333;
            color: white;
            padding: 20px 0;
            text-align: center;
        }
        
        nav {
            display: flex;
            flex-wrap: wrap;
            background-color: #444;
        }
        
        nav a {
            color: white;
            text-decoration: none;
            padding: 15px 20px;
            text-align: center;
            flex-grow: 1;
        }
        
        nav a:hover {
            background-color: #555;
        }
        
        .row {
            display: flex;
            flex-wrap: wrap;
            margin: 0 -15px;
        }
        
        .column {
            padding: 0 15px;
            margin-bottom: 20px;
        }
        
        /* Desktop layout */
        @media (min-width: 768px) {
            .container {
                max-width: 1140px;
            }
            
            .column {
                flex: 0 0 33.333333%;
            }
        }
        
        /* Tablet layout */
        @media (min-width: 576px) and (max-width: 767px) {
            .column {
                flex: 0 0 50%;
            }
        }
        
        /* Mobile layout */
        @media (max-width: 575px) {
            nav {
                flex-direction: column;
            }
            
            .column {
                flex: 0 0 100%;
            }
        }
        
        footer {
            background-color: #333;
            color: white;
            text-align: center;
            padding: 20px 0;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <header>
        <div class="container">
            <h1>Responsive Website</h1>
        </div>
    </header>
    
    <nav>
        <a href="#">Home</a>
        <a href="#">About</a>
        <a href="#">Services</a>
        <a href="#">Gallery</a>
        <a href="#">Contact</a>
    </nav>
    
    <div class="container">
        <div class="row">
            <div class="column">
                <h2>Column 1</h2>
                <p>Content for the first column goes here...</p>
            </div>
            <div class="column">
                <h2>Column 2</h2>
                <p>Content for the second column goes here...</p>
            </div>
            <div class="column">
                <h2>Column 3</h2>
                <p>Content for the third column goes here...</p>
            </div>
        </div>
    </div>
    
    <footer>
        <div class="container">
            <p>&copy; 2025 Responsive Website</p>
        </div>
    </footer>
</body>
</html>
```

### Practical CSS Examples

#### Navigation Menu

```css
/* Basic horizontal navigation */
.nav {
    list-style-type: none;
    margin: 0;
    padding: 0;
    background-color: #333;
    overflow: hidden;
}

.nav li {
    float: left;
}

.nav li a {
    display: block;
    color: white;
    text-align: center;
    padding: 14px 16px;
    text-decoration: none;
    transition: background-color 0.3s;
}

.nav li a:hover {
    background-color: #555;
}

.nav li a.active {
    background-color: #4CAF50;
}

/* Responsive navigation */
@media screen and (max-width: 600px) {
    .nav li {
        float: none;
    }
}
```

#### Card Layout

```css
.card {
    box-shadow: 0 4px 8px rgba(0,0,0,0.1);
    border-radius: 8px;
    overflow: hidden;
    margin-bottom: 20px;
    transition: transform 0.3s, box-shadow 0.3s;
}

.card:hover {
    transform: translateY(-5px);
    box-shadow: 0 8px 16px rgba(0,0,0,0.2);
}

.card-image {
    width: 100%;
    height: 200px;
    object-fit: cover;
}

.card-content {
    padding: 20px;
}

.card-title {
    margin-top: 0;
    margin-bottom: 10px;
    color: #333;
}
.card-text {
    color: #666;
    line-height: 1.6;
    font-size: 14px;
}

.card-button {
    display: inline-block;
    background-color: #3498db;
    color: white;
    padding: 8px 16px;
    text-decoration: none;
    border-radius: 4px;
    margin-top: 15px;
    transition: background-color 0.3s;
}

.card-button:hover {
    background-color: #2980b9;
}

#### Grid Layout System

```css
.grid-container {
    display: grid;
    grid-template-columns: repeat(12, 1fr);
    grid-gap: 20px;
}

.grid-item-full {
    grid-column: span 12;
}

.grid-item-half {
    grid-column: span 6;
}

.grid-item-third {
    grid-column: span 4;
}

.grid-item-quarter {
    grid-column: span 3;
}

/* Responsive adjustments */
@media (max-width: 768px) {
    .grid-item-half,
    .grid-item-third,
    .grid-item-quarter {
        grid-column: span 6;
    }
}

@media (max-width: 480px) {
    .grid-item-half,
    .grid-item-third,
    .grid-item-quarter {
        grid-column: span 12;
    }
}
```

#### Form Styling

```css
.form-group {
    margin-bottom: 20px;
}

.form-label {
    display: block;
    margin-bottom: 8px;
    font-weight: bold;
    color: #333;
}

.form-input {
    width: 100%;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 4px;
    font-size: 16px;
    transition: border-color 0.3s, box-shadow 0.3s;
}

.form-input:focus {
    border-color: #3498db;
    box-shadow: 0 0 5px rgba(52, 152, 219, 0.5);
    outline: none;
}

.form-input.error {
    border-color: #e74c3c;
}

.error-message {
    color: #e74c3c;
    font-size: 12px;
    margin-top: 5px;
}

.form-button {
    background-color: #3498db;
    color: white;
    border: none;
    padding: 12px 20px;
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.3s;
}

.form-button:hover {
    background-color: #2980b9;
}

.form-button:disabled {
    background-color: #95a5a6;
    cursor: not-allowed;
}
```

#### Animated Elements

```css
/* Fade-in animation */
@keyframes fadeIn {
    from {
        opacity: 0;
    }
    to {
        opacity: 1;
    }
}

.fade-in {
    animation: fadeIn 1s ease-in-out;
}

/* Slide-in animation */
@keyframes slideIn {
    from {
        transform: translateY(50px);
        opacity: 0;
    }
    to {
        transform: translateY(0);
        opacity: 1;
    }
}

.slide-in {
    animation: slideIn 0.8s ease-out forwards;
}

/* Staggered animations for multiple elements */
.staggered-item:nth-child(1) {
    animation-delay: 0.1s;
}

.staggered-item:nth-child(2) {
    animation-delay: 0.2s;
}

.staggered-item:nth-child(3) {
    animation-delay: 0.3s;
}
```

#### Custom CSS Variables (CSS Custom Properties)

```css
:root {
    /* Colors */
    --primary-color: #3498db;
    --secondary-color: #2ecc71;
    --accent-color: #f1c40f;
    --text-color: #333;
    --bg-color: #f9f9f9;
    
    /* Typography */
    --base-font-size: 16px;
    --heading-font: 'Helvetica Neue', sans-serif;
    --body-font: 'Arial', sans-serif;
    
    /* Spacing */
    --spacing-small: 8px;
    --spacing-medium: 16px;
    --spacing-large: 24px;
    
    /* Border radius */
    --border-radius: 4px;
    
    /* Transitions */
    --transition-speed: 0.3s;
}

/* Using variables */
body {
    font-family: var(--body-font);
    font-size: var(--base-font-size);
    color: var(--text-color);
    background-color: var(--bg-color);
    line-height: 1.6;
}

h1, h2, h3, h4, h5, h6 {
    font-family: var(--heading-font);
}

.button {
    background-color: var(--primary-color);
    padding: var(--spacing-small) var(--spacing-medium);
    border-radius: var(--border-radius);
    transition: background-color var(--transition-speed);
}

.button:hover {
    background-color: #2980b9; /* Darker shade of primary color */
}

/* Changing variables for dark mode */
@media (prefers-color-scheme: dark) {
    :root {
        --text-color: #f0f0f0;
        --bg-color: #222;
    }
}
```

### CSS Best Practices

1. **Use a CSS Reset or Normalize CSS**
   ```css
   /* Simple CSS Reset */
   * {
       margin: 0;
       padding: 0;
       box-sizing: border-box;
   }
   ```

2. **Follow a Naming Convention**
   
   BEM (Block Element Modifier) Example:
   ```css
   /* Block component */
   .card {
       background-color: white;
       border-radius: 4px;
   }

   /* Element that depends on the block */
   .card__title {
       font-size: 18px;
       font-weight: bold;
   }

   .card__image {
       width: 100%;
   }

   /* Modifier that changes the style of the block */
   .card--featured {
       border: 2px solid gold;
   }
   ```

3. **Organize CSS with Comments**
   ```css
   /* ==========================================================================
      Header Styles
      ========================================================================== */
   
   .header {
       /* Header styles */
   }
   
   /* Navigation */
   .nav {
       /* Navigation styles */
   }
   
   /* ==========================================================================
      Main Content
      ========================================================================== */
   
   /* Articles */
   .article {
       /* Article styles */
   }
   ```

4. **Minimize Specificity Issues**
   
   Avoid:
   ```css
   #header .nav ul li a { /* High specificity, hard to override */
       color: blue;
   }
   ```
   
   Better:
   ```css
   .nav-link { /* Lower specificity, easier to manage */
       color: blue;
   }
   ```

5. **Use Shorthand Properties**
   
   Instead of:
   ```css
   .element {
       margin-top: 10px;
       margin-right: 15px;
       margin-bottom: 10px;
       margin-left: 15px;
       
       padding-top: 5px;
       padding-right: 10px;
       padding-bottom: 5px;
       padding-left: 10px;
   }
   ```
   
   Use:
   ```css
   .element {
       margin: 10px 15px;
       padding: 5px 10px;
   }
   ```

6. **Avoid !important**
   
   Only use `!important` as a last resort as it breaks the natural cascading of CSS:
   
   ```css
   /* Avoid */
   .element {
       color: blue !important;
   }
   
   /* Better: use more specific selectors or refactor your CSS */
   ```

7. **Use Media Queries Effectively**
   
   ```css
   /* Mobile first approach */
   .container {
       width: 100%; /* Default for mobile */
   }
   
   /* Tablet and up */
   @media (min-width: 768px) {
       .container {
           width: 750px;
       }
   }
   
   /* Desktop */
   @media (min-width: 992px) {
       .container {
           width: 970px;
       }
   }
   
   /* Large desktop */
   @media (min-width: 1200px) {
       .container {
           width: 1170px;
       }
   }
   ```

8. **Optimize Performance**
   
   - Minify CSS files for production
   - Use CSS sprites for multiple icons
   - Avoid complex selectors
   - Use efficient properties (prefer `transform` and `opacity` for animations)

### CSS Frameworks and Libraries

While learning CSS fundamentals is essential, CSS frameworks can help with rapid development:

1. **Bootstrap**
   - Popular CSS framework for responsive, mobile-first websites
   - Grid system, pre-styled components, utilities
   
2. **Tailwind CSS**
   - Utility-first CSS framework
   - Allows building custom designs without leaving HTML
   
3. **Foundation**
   - Advanced responsive front-end framework
   - Flexible grid system and UI components
   
4. **Bulma**
   - Modern CSS framework based on Flexbox
   - Modular architecture, no JavaScript dependencies
   
5. **Materialize**
   - Framework based on Material Design by Google
   - Responsive and interactive components

### CSS Preprocessors

CSS preprocessors extend CSS with variables, nesting, mixins, functions, and more:

1. **Sass/SCSS**
   ```scss
   // Variables
   $primary-color: #3498db;
   $padding: 15px;
   
   // Nesting
   .container {
       max-width: 1200px;
       margin: 0 auto;
       
       .header {
           background-color: $primary-color;
           padding: $padding;
           
           h1 {
               color: white;
           }
       }
   }
   
   // Mixins
   @mixin border-radius($radius) {
       -webkit-border-radius: $radius;
       -moz-border-radius: $radius;
       border-radius: $radius;
   }
   
   .button {
       @include border-radius(5px);
   }
   
   // Extends
   %message-shared {
       border: 1px solid #ccc;
       padding: 10px;
       color: #333;
   }
   
   .success {
       @extend %message-shared;
       border-color: green;
   }
   
   .error {
       @extend %message-shared;
       border-color: red;
   }
   ```

2. **Less**
   ```less
   // Variables
   @primary-color: #3498db;
   @padding: 15px;
   
   // Nesting
   .container {
       max-width: 1200px;
       margin: 0 auto;
       
       .header {
           background-color: @primary-color;
           padding: @padding;
           
           h1 {
               color: white;
           }
       }
   }
   
   // Mixins
   .border-radius(@radius) {
       -webkit-border-radius: @radius;
       -moz-border-radius: @radius;
       border-radius: @radius;
   }
   
   .button {
       .border-radius(5px);
   }
   ```

### CSS Tools and Resources

1. **Design Tools with CSS Export**
   - Figma
   - Adobe XD
   - Sketch

2. **CSS Generators**
   - CSS Gradient Generators
   - Flexbox Generators
   - CSS Grid Generators
   - Animation Generators

3. **CSS Validation and Testing**
   - W3C CSS Validator
   - CSS Lint
   - Browser Developer Tools

4. **Learning Resources**
   - MDN Web Docs (Mozilla Developer Network)
   - CSS-Tricks
   - W3Schools
   - freeCodeCamp

### Exercise Examples

1. **Create a responsive navigation bar that collapses into a mobile menu on small screens**
2. **Design a card layout that works across different screen sizes**
3. **Implement a CSS-only image slider/carousel**
4. **Create a form with custom styled inputs, radio buttons, and checkboxes**
5. **Build a responsive grid layout system from scratch**
6. **Create animated buttons with hover effects**
7. **Design a dark/light theme switcher using CSS variables**
8. **Create a fixed header that changes style on scroll**
9. **Implement different types of loading animations**
10. **Design a responsive photo gallery with CSS Grid**