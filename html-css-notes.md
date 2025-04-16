# HTML and CSS: Student Notes

## Unit 1: HTML and CSS (15 Hours)

### HTML Basics

#### HTML Tag Reference

HTML (HyperText Markup Language) is the standard markup language for creating web pages. It describes the structure of a web page using elements represented by tags.

**HTML Document Structure:**
```html
<!DOCTYPE html>
<html>
<head>
    <title>Page Title</title>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>
    <!-- Content goes here -->
</body>
</html>
```

#### Global Attributes

Global attributes can be used with any HTML element:

| Attribute | Description |
|-----------|-------------|
| `class` | Specifies one or more class names for an element |
| `id` | Specifies a unique id for an element |
| `style` | Specifies inline CSS style for an element |
| `title` | Specifies extra information about an element (displayed as tooltip) |
| `lang` | Specifies the language of the element's content |
| `data-*` | Used to store custom data private to the page or application |
| `hidden` | Specifies that an element is not yet, or is no longer, relevant |

#### Document Structure Tags

| Tag | Description |
|-----|-------------|
| `<!DOCTYPE>` | Defines the document type |
| `<html>` | Defines an HTML document |
| `<head>` | Contains metadata/information for the document |
| `<title>` | Defines a title for the document |
| `<body>` | Defines the document's body |
| `<h1>` to `<h6>` | Defines HTML headings |
| `<p>` | Defines a paragraph |
| `<br>` | Inserts a single line break |
| `<hr>` | Defines a thematic change in the content |

#### Formatting Tags

| Tag | Description |
|-----|-------------|
| `<b>` | Bold text |
| `<strong>` | Important text (semantically strong emphasis) |
| `<i>` | Italic text |
| `<em>` | Emphasized text (semantically emphasized) |
| `<mark>` | Marked/highlighted text |
| `<small>` | Smaller text |
| `<del>` | Deleted text |
| `<ins>` | Inserted text |
| `<sub>` | Subscript text |
| `<sup>` | Superscript text |
| `<q>` | Short quotation |
| `<blockquote>` | Section quoted from another source |
| `<abbr>` | Abbreviation or acronym |
| `<address>` | Contact information for author/owner |
| `<cite>` | Title of a work |
| `<code>` | Computer code text |

#### Text Level Formatting

Text level formatting tags provide semantic meaning and visual styling to text:

```html
<p>This is <b>bold</b> and this is <strong>strongly emphasized</strong>.</p>
<p>This is <i>italic</i> and this is <em>emphasized</em>.</p>
<p>This is <mark>highlighted</mark> text.</p>
<p>This is <small>smaller</small> text.</p>
<p>This is <del>deleted</del> and this is <ins>inserted</ins> text.</p>
<p>This is <sub>subscript</sub> and this is <sup>superscript</sup>.</p>
```

#### Block Level Formatting

Block level elements start on a new line and take up the full available width:

| Tag | Description |
|-----|-------------|
| `<div>` | Defines a division or section |
| `<h1>` to `<h6>` | Headings |
| `<p>` | Paragraph |
| `<pre>` | Preformatted text |
| `<blockquote>` | Quotation |
| `<ol>` | Ordered list |
| `<ul>` | Unordered list |
| `<li>` | List item |
| `<dl>` | Description list |
| `<dt>` | Term in description list |
| `<dd>` | Description in description list |
| `<figure>` | Self-contained content |
| `<figcaption>` | Caption for a figure element |

Example:
```html
<div class="container">
    <h1>Main Heading</h1>
    <p>This is a paragraph of text.</p>
    <blockquote>
        This is a blockquote. It's usually indented to separate it from regular text.
    </blockquote>
</div>
```

### List Tags

#### Unordered Lists
```html
<ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
</ul>
```

#### Ordered Lists
```html
<ol>
    <li>First item</li>
    <li>Second item</li>
    <li>Third item</li>
</ol>
```

#### Definition Lists
```html
<dl>
    <dt>HTML</dt>
    <dd>HyperText Markup Language - the standard language for creating web pages</dd>
    <dt>CSS</dt>
    <dd>Cascading Style Sheets - used for styling web pages</dd>
</dl>
```

#### Nested Lists
```html
<ul>
    <li>Main item 1
        <ul>
            <li>Sub-item 1.1</li>
            <li>Sub-item 1.2</li>
        </ul>
    </li>
    <li>Main item 2
        <ol>
            <li>Numbered sub-item 2.1</li>
            <li>Numbered sub-item 2.2</li>
        </ol>
    </li>
</ul>
```

### Hyperlink Tags

#### Basic Links
```html
<a href="https://www.example.com">Visit Example.com</a>
```

#### Link to Email Address
```html
<a href="mailto:someone@example.com">Send Email</a>
```

#### Link to Phone Number
```html
<a href="tel:+1234567890">Call Us</a>
```

#### Link to a Specific Part of the Page
```html
<!-- The target -->
<h2 id="section2">Section 2</h2>

<!-- The link to the target -->
<a href="#section2">Go to Section 2</a>
```

#### Link Attributes

| Attribute | Description |
|-----------|-------------|
| `href` | Specifies the URL of the page the link goes to |
| `target` | Specifies where to open the linked document (`_blank`, `_self`, `_parent`, `_top`) |
| `download` | Specifies that the target will be downloaded when clicked |
| `rel` | Specifies the relationship between the current and linked document |
| `title` | Specifies extra information about the link (tooltip) |

### Executable Content Tags

Tags that can include or execute content:

| Tag | Description |
|-----|-------------|
| `<script>` | Defines a client-side script (JavaScript) |
| `<noscript>` | Defines alternate content for users without script support |
| `<canvas>` | Used to draw graphics via JavaScript |
| `<svg>` | Container for SVG graphics |
| `<audio>` | Embeds sound content |
| `<video>` | Embeds video content |
| `<iframe>` | Embeds another HTML page within the current page |

Example:
```html
<!-- JavaScript -->
<script>
    function sayHello() {
        alert("Hello, World!");
    }
</script>
<button onclick="sayHello()">Say Hello</button>

<!-- Embedded content -->
<iframe src="https://www.example.com" width="500" height="300"></iframe>

<!-- Media -->
<audio controls>
    <source src="audio.mp3" type="audio/mpeg">
    Your browser does not support the audio element.
</audio>

<video width="320" height="240" controls>
    <source src="video.mp4" type="video/mp4">
    Your browser does not support the video element.
</video>
```

### Images & Imagemaps

#### Basic Image
```html
<img src="image.jpg" alt="Description of image">
```

#### Image Attributes

| Attribute | Description |
|-----------|-------------|
| `src` | Specifies the path to the image |
| `alt` | Specifies an alternate text for the image |
| `width` | Specifies the width of the image |
| `height` | Specifies the height of the image |
| `loading` | Specifies whether to lazy load the image (`eager` or `lazy`) |
| `usemap` | Specifies an image as a client-side image map |

#### Client-Side Imagemaps

An image map allows you to define clickable areas on an image:

```html
<img src="workplace.jpg" alt="Workplace" usemap="#workmap" width="400" height="379">

<map name="workmap">
  <area shape="rect" coords="34,44,270,350" alt="Computer" href="computer.htm">
  <area shape="rect" coords="290,172,333,250" alt="Phone" href="phone.htm">
  <area shape="circle" coords="337,300,44" alt="Coffee" href="coffee.htm">
</map>
```

The `<area>` tag has these key attributes:
- `shape`: Defines the shape of the area (`rect`, `circle`, `poly`)
- `coords`: Specifies the coordinates of the area
- `href`: Specifies the destination link
- `alt`: Provides alternative text

#### Server-Side Imagemaps

For server-side image maps, the coordinates are sent to a server program:

```html
<a href="server_script.php">
    <img src="workplace.jpg" alt="Workplace" ismap>
</a>
```

The `ismap` attribute converts the image into a server-side image map.

#### Using Server-Side and Client-Side Imagemaps Together

You can combine both approaches:

```html
<a href="server_script.php">
    <img src="workplace.jpg" alt="Workplace" ismap usemap="#workmap">
</a>

<map name="workmap">
    <area shape="rect" coords="34,44,270,350" alt="Computer" href="computer.htm">
    <area shape="circle" coords="337,300,44" alt="Coffee" href="coffee.htm">
</map>
```

#### Alternative Text for Imagemaps

Always provide alternative text for accessibility:

1. For the image: Use the `alt` attribute in the `<img>` tag
2. For each clickable area: Use the `alt` attribute in each `<area>` tag

This helps users with screen readers understand the purpose of the image and its clickable regions.

### Tables

#### Introduction to HTML Tables

Tables are used to organize data in rows and columns. They consist of:
- `<table>`: Container for the entire table
- `<tr>`: Table row
- `<th>`: Table header cell
- `<td>`: Table data cell

#### Basic Table Structure

```html
<table>
    <tr>
        <th>Header 1</th>
        <th>Header 2</th>
    </tr>
    <tr>
        <td>Row 1, Cell 1</td>
        <td>Row 1, Cell 2</td>
    </tr>
    <tr>
        <td>Row 2, Cell 1</td>
        <td>Row 2, Cell 2</td>
    </tr>
</table>
```

#### Table Tags

| Tag | Description |
|-----|-------------|
| `<table>` | Defines a table |
| `<tr>` | Defines a row in a table |
| `<th>` | Defines a header cell in a table |
| `<td>` | Defines a regular cell in a table |
| `<caption>` | Defines a table caption |
| `<thead>` | Groups the header content in a table |
| `<tbody>` | Groups the body content in a table |
| `<tfoot>` | Groups the footer content in a table |
| `<colgroup>` | Specifies a group of columns for formatting |
| `<col>` | Specifies column properties for each column within a `<colgroup>` |

#### Alignment

##### Aligning Entire Table

```html
<div style="text-align: center;">
    <table>
        <!-- table content -->
    </table>
</div>
```

##### Alignment within a Row

```html
<tr style="text-align: right;">
    <td>Cell 1</td>
    <td>Cell 2</td>
</tr>
```

##### Alignment within a Cell

```html
<td style="text-align: center; vertical-align: middle;">Cell content</td>
```

#### Table Attributes

| Attribute | Description |
|-----------|-------------|
| `border` | Specifies the width of the border (HTML5 use CSS instead) |
| `cellpadding` | Specifies the space between cell content and cell border (HTML5 use CSS instead) |
| `cellspacing` | Specifies the space between cells (HTML5 use CSS instead) |
| `width` | Specifies the width of the table (HTML5 use CSS instead) |

#### Content Summary

Tables can contain:
- Text
- Images
- Lists
- Other tables
- Forms
- Any other HTML elements

#### Background Color

```html
<table style="background-color: #f1f1f1;">
    <tr>
        <td style="background-color: #ffffff;">White background</td>
        <td style="background-color: #e0e0e0;">Gray background</td>
    </tr>
</table>
```

#### Adding a Caption

```html
<table>
    <caption>Monthly Savings</caption>
    <tr>
        <th>Month</th>
        <th>Savings</th>
    </tr>
    <tr>
        <td>January</td>
        <td>$100</td>
    </tr>
</table>
```

#### Setting the Width

```html
<table style="width: 100%;">
    <tr>
        <td style="width: 30%;">Column 1 (30% width)</td>
        <td style="width: 70%;">Column 2 (70% width)</td>
    </tr>
</table>
```

#### Adding a Border

```html
<table style="border: 1px solid black; border-collapse: collapse;">
    <tr>
        <td style="border: 1px solid black;">Cell with border</td>
        <td style="border: 1px solid black;">Cell with border</td>
    </tr>
</table>
```

#### Spacing Within a Cell (Padding)

```html
<table>
    <tr>
        <td style="padding: 15px;">Cell with padding</td>
    </tr>
</table>
```

#### Spacing Between Cells

```html
<table style="border-spacing: 10px;">
    <tr>
        <td>Cell 1</td>
        <td>Cell 2</td>
    </tr>
</table>
```

#### Spanning Multiple Rows or Columns

##### Column Spanning
```html
<table>
    <tr>
        <th colspan="2">Name</th>
        <th>Age</th>
    </tr>
    <tr>
        <td>First</td>
        <td>Last</td>
        <td>25</td>
    </tr>
</table>
```

##### Row Spanning
```html
<table>
    <tr>
        <th>Name</th>
        <td>John</td>
    </tr>
    <tr>
        <th rowspan="2">Phone</th>
        <td>555-1234</td>
    </tr>
    <tr>
        <td>555-5678</td>
    </tr>
</table>
```

#### Table Sections and Column Properties

```html
<table>
    <colgroup>
        <col style="background-color: #f1f1f1">
        <col style="background-color: #e0e0e0">
    </colgroup>
    <thead>
        <tr>
            <th>Header 1</th>
            <th>Header 2</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>Data 1</td>
            <td>Data 2</td>
        </tr>
    </tbody>
    <tfoot>
        <tr>
            <td>Footer 1</td>
            <td>Footer 2</td>
        </tr>
    </tfoot>
</table>
```

#### Tables as a Design Tool

While tables were historically used for layout, modern web design uses CSS for layout instead. Tables should only be used for tabular data. However, understanding table structure is important:

```html
<table border="0" cellpadding="0" cellspacing="0" width="100%">
    <tr>
        <td width="25%">Navigation</td>
        <td width="75%">Content</td>
    </tr>
</table>
```

### Frames

#### Introduction to Frames

Frames allow multiple HTML documents to be displayed in a single browser window. Each HTML document is displayed in its own section, or frame.

**Note**: Frames are obsolete in HTML5. Modern web development uses CSS and JavaScript for layout and content management instead. However, understanding frames is useful for maintaining legacy code.

#### Applications of Frames

- Navigation systems that keep navigation controls visible while content changes
- Displaying multiple documents simultaneously
- Keeping certain content (like headers, footers, menus) static while other content scrolls

#### Frames Document

A frames document uses the `<frameset>` tag instead of `<body>`:

```html
<!DOCTYPE html>
<html>
<head>
    <title>Frameset Example</title>
</head>
<frameset rows="100,*">
    <frame src="header.html" name="header">
    <frameset cols="20%,80%">
        <frame src="menu.html" name="menu">
        <frame src="content.html" name="content">
    </frameset>
</frameset>
</html>
```

#### The `<frameset>` Tag

The `<frameset>` tag defines how to divide the window into frames:

- `cols`: Specifies the number and size of columns
- `rows`: Specifies the number and size of rows

Size values can be:
- Pixels (e.g., `100px`)
- Percentage (e.g., `20%`)
- Relative (e.g., `*`)

#### Nesting `<frameset>` Tags

You can nest framesets to create complex layouts:

```html
<frameset rows="15%,*,10%">
    <frame src="header.html">
    <frameset cols="20%,*">
        <frame src="menu.html">
        <frame src="content.html">
    </frameset>
    <frame src="footer.html">
</frameset>
```

#### Placing Content in Frames with the `<frame>` Tag

The `<frame>` tag defines individual frames within a frameset:

```html
<frame src="page.html" name="frameName" scrolling="auto" noresize>
```

Attributes:
- `src`: Specifies the document to display
- `name`: Names the frame (for targeting)
- `scrolling`: Controls scrollbars (`yes`, `no`, `auto`)
- `noresize`: Prevents users from resizing the frame
- `frameborder`: Specifies whether to display a border (`1` or `0`)
- `marginwidth`: Margin between frame content and left/right edges
- `marginheight`: Margin between frame content and top/bottom edges

#### Targeting Named Frames

Links can target specific frames using the `target` attribute:

```html
<!-- In menu.html -->
<a href="page1.html" target="content">Page 1</a>
<a href="page2.html" target="content">Page 2</a>
```

Special target names:
- `_self`: Opens in the same frame
- `_parent`: Opens in the parent frameset
- `_top`: Opens in the full body of the window
- `_blank`: Opens in a new window or tab

#### Creating Floating Frames

Inline frames (`<iframe>`) embed a document within the current HTML document:

```html
<iframe src="page.html" width="400" height="300" style="border:none;"></iframe>
```

Attributes:
- `src`: Specifies the URL of the document
- `width`, `height`: Dimensions
- `name`: For targeting
- `sandbox`: Security restrictions
- `allow`: Feature policy

#### Using Hidden Frames

Hidden frames can run scripts or store data without being visible:

```html
<frameset rows="100%,*">
    <frame src="visible.html" name="visible">
    <frame src="hidden.html" name="hidden" scrolling="no" noresize>
</frameset>
```

Or with inline frames:

```html
<iframe src="hidden.html" style="display:none"></iframe>
```

### Forms

#### Creating Forms

Forms are used to collect user input. The `<form>` element is a container for different types of input elements.

```html
<form action="process.php" method="post">
    <!-- Form elements go here -->
    <input type="submit" value="Submit">
</form>
```

#### The `<form>` Tag

Key attributes:
- `action`: URL where form data is sent
- `method`: HTTP method (`get` or `post`)
- `target`: Where to display the response
- `enctype`: How form data is encoded (important for file uploads)
- `autocomplete`: Enable/disable browser autocomplete
- `novalidate`: Skip form validation

#### Named Input Fields

Named inputs allow server-side scripts to identify form data:

```html
<input type="text" name="username">
```

The `name` attribute is essential for form processing.

#### The `<input>` Tag

The `<input>` element is the most common form element with many different types:

| Type | Description |
|------|-------------|
| `text` | Single-line text input |
| `password` | Password field (masked text) |
| `radio` | Radio button (select one) |
| `checkbox` | Checkbox (select multiple) |
| `submit` | Submit button |
| `reset` | Reset button |
| `file` | File upload control |
| `hidden` | Hidden input field |
| `button` | Clickable button |
| `email` | Input for email addresses |
| `url` | Input for URLs |
| `number` | Input for numeric values |
| `range` | Slider control for numbers |
| `date` | Date picker |
| `color` | Color picker |
| `search` | Search field |

#### Multiple Lines Text Windows

For multi-line input, use the `<textarea>` element:

```html
<textarea name="comments" rows="5" cols="40">
Default text can go here
</textarea>
```

Attributes:
- `rows`: Visible number of lines
- `cols`: Visible width
- `maxlength`: Maximum number of characters
- `wrap`: Text wrapping (`soft`, `hard`)

#### Drop Down and List Boxes

##### Select Dropdown
```html
<select name="country">
    <option value="usa">United States</option>
    <option value="canada">Canada</option>
    <option value="uk">United Kingdom</option>
</select>
```

##### Multiple Selection List
```html
<select name="languages" multiple size="4">
    <option value="html">HTML</option>
    <option value="css">CSS</option>
    <option value="js">JavaScript</option>
    <option value="php">PHP</option>
</select>
```

##### Option Groups
```html
<select name="cars">
    <optgroup label="European Cars">
        <option value="volvo">Volvo</option>
        <option value="bmw">BMW</option>
    </optgroup>
    <optgroup label="American Cars">
        <option value="ford">Ford</option>
        <option value="chevy">Chevrolet</option>
    </optgroup>
</select>
```

#### Hidden, Text, Text Area, Password

```html
<input type="hidden" name="user_id" value="12345">
<input type="text" name="username" placeholder="Enter username">
<textarea name="bio" placeholder="Tell us about yourself"></textarea>
<input type="password" name="password" placeholder="Enter password">
```

#### File Upload

```html
<form action="upload.php" method="post" enctype="multipart/form-data">
    <input type="file" name="fileUpload">
    <input type="submit" value="Upload">
</form>
```

**Note**: For file uploads, the form must use:
- `method="post"`
- `enctype="multipart/form-data"`

#### Button, Submit, Reset

```html
<input type="button" value="Click Me" onclick="alert('Button clicked!')">
<input type="submit" value="Submit Form">
<input type="reset" value="Reset Form">

<!-- Button element alternative -->
<button type="button">Click Me</button>
<button type="submit">Submit Form</button>
<button type="reset">Reset Form</button>
```

#### Radio, Checkbox

##### Radio Buttons (select one)
```html
<input type="radio" name="gender" value="male" id="male">
<label for="male">Male</label>
<input type="radio" name="gender" value="female" id="female">
<label for="female">Female</label>
```

##### Checkboxes (select multiple)
```html
<input type="checkbox" name="interests" value="sports" id="sports">
<label for="sports">Sports</label>
<input type="checkbox" name="interests" value="music" id="music">
<label for="music">Music</label>
<input type="checkbox" name="interests" value="reading" id="reading">
<label for="reading">Reading</label>
```

#### Select, Option

As shown in the "Drop Down and List Boxes" section above.

#### Forms and Scripting

Forms can interact with JavaScript:

```html
<form id="myForm" onsubmit="return validateForm()">
    <input type="text" id="username" name="username">
    <input type="submit" value="Submit">
</form>

<script>
function validateForm() {
    var username = document.getElementById("username").value;
    if (username == "") {
        alert("Username must be filled out");
        return false;
    }
    return true;
}
</script>
```

#### Action Buttons

Action buttons can trigger specific behaviors:

```html
<button type="button" onclick="doSomething()">Action Button</button>

<script>
function doSomething() {
    // Custom JavaScript code
    alert("Action performed!");
}
</script>
```

#### Labeling Input Fields

Labels improve usability and accessibility:

```html
<label for="username">Username:</label>
<input type="text" id="username" name="username">

<!-- Alternate method -->
<label>
    Email Address:
    <input type="email" name="email">
</label>
```

#### Grouping Related Fields

The `<fieldset>` and `<legend>` elements group related form controls:

```html
<fieldset>
    <legend>Personal Information</legend>
    <label for="name">Name:</label>
    <input type="text" id="name" name="name"><br>
    
    <label for="email">Email:</label>
    <input type="email" id="email" name="email">
</fieldset>

<fieldset>
    <legend>Shipping Address</legend>
    <label for="address">Address:</label>
    <input type="text" id="address" name="address"><br>
    
    <label for="city">City:</label>
    <input type="text" id="city" name="city">
</fieldset>
```

#### Disabled and Read-only Fields

```html
<!-- Disabled - cannot be changed, not submitted with form -->
<input type="text" name="username" value="johndoe" disabled>

<!-- Read-only - cannot be changed, but submitted with form -->
<input type="text" name="username" value="johndoe" readonly>
```

#### Form Field Event Handlers

Common event handlers for form elements:

```html
<input type="text" name="username" 
       onchange="handleChange()" 
       onfocus="handleFocus()" 
       onblur="handleBlur()"
       oninput="handleInput()">

<script>
function handleChange() {
    console.log("Value changed and field lost focus");
}

function handleFocus() {
    console.log("Field received focus");
}

function handleBlur() {
    console.log("Field lost focus");
}

function handleInput() {
    console.log("Value changed during input");
}
</script>
```

#### Passing Form Data

Form data can be passed using two methods:

1. **GET Method**:
   - Appends data to URL as query parameters
   - Limited data length (about 2048 characters)
   - Bookmarkable
   - Not secure for sensitive data
   - Suitable for search forms

```html
<form action="search.php" method="get">
    <input type="text" name="query">
    <input type="submit" value="Search">
</form>
```

2. **POST Method**:
   - Sends data in the HTTP request body
   - No size limitations
   - Not bookmarkable
   - More secure (but not encrypted)
   - Suitable for most forms, especially with sensitive data or file uploads

```html
<form action="process.php" method="post">
    <input type="text" name="username">
    <input type="password" name="password">
    <input type="submit" value="Login">
</form>
```

### Style Sheets

#### Definition

Cascading Style Sheets (CSS) is a style sheet language used for describing the presentation of a document written in HTML. CSS describes how elements should be rendered on screen, on paper, in speech, or on other media.

#### Importance

CSS is important because it:
- Separates content (HTML) from presentation (CSS)
- Enables consistent styling across multiple pages
- Makes site maintenance easier
- Reduces file size and loading time
- Provides extensive layout and design capabilities
- Supports responsive design for different devices
- Improves accessibility

#### Different Approaches to Style Sheets

There are three ways to include CSS in an HTML document:

1. **Inline CSS**: Using the `style` attribute on individual HTML elements
2. **Internal CSS**: Using the `<style>` tag in the document head
3. **External CSS**: Linking to an external CSS file using the `<link>` tag

#### Using Multiple Approaches

You can combine different CSS approaches, following the precedence order:
1. Inline styles (highest priority)
2. Internal style sheets
3. External style sheets
4. Browser defaults (lowest priority)

```html
<!DOCTYPE html>
<html>
<head>
    <!-- External CSS -->
    <link rel="stylesheet" href="styles.css">
    
    <!-- Internal CSS -->
    <style>
        p { color: blue; }
    </style>
</head>
<body>
    <!-- Inline CSS -->
    <p style="color: red;">This text will be red, overriding both external and internal styles.</p>
    
    <p>This text will be blue, from the internal style sheet.</p>
</body>
</html>
```

#### Linking to Style Information in Separate File

External CSS is linked using the `<link>` tag in the `<head>` section:

```html
<head>
    <link rel="stylesheet" type="text/css" href="styles.css">
</head>
```

You can link multiple stylesheets:

```html
<head>
    <link rel="stylesheet" type="text/css" href="base.css">
    <link rel="stylesheet" type="text/css" href="layout.css">
    <link rel="stylesheet" type="