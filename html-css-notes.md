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

#### Understanding `<div>` and `<span>` Elements

##### The `<div>` Element (Block-level Container)

The `<div>` element is a generic block-level container used to group content for styling and layout purposes. It takes up the full width available and starts on a new line.

**Basic `<div>` Example:**
```html
<div>
    <h2>Welcome to My Website</h2>
    <p>This is a simple div containing content.</p>
</div>
```

**Using `<div>` for Layout Sections:**
```html
<div class="header">
    <h1>Website Title</h1>
    <nav>
        <a href="#home">Home</a>
        <a href="#about">About</a>
        <a href="#contact">Contact</a>
    </nav>
</div>

<div class="content">
    <div class="sidebar">
        <h3>Navigation</h3>
        <ul>
            <li><a href="#section1">Section 1</a></li>
            <li><a href="#section2">Section 2</a></li>
        </ul>
    </div>

    <div class="main">
        <h2>Main Content Area</h2>
        <p>This is the main content of the page.</p>
    </div>
</div>

<div class="footer">
    <p>&copy; 2024 My Website. All rights reserved.</p>
</div>
```

**Using `<div>` with Inline CSS:**
```html
<div style="background-color: #f0f0f0; padding: 20px; margin: 10px; border: 1px solid #ccc;">
    <h3>Styled Container</h3>
    <p>This div has background color, padding, margin, and border.</p>
</div>
```

**Nested `<div>` Elements:**
```html
<div class="card">
    <div class="card-header">
        <h3>Product Card</h3>
    </div>
    <div class="card-body">
        <p>Product description goes here.</p>
        <p>Price: $29.99</p>
    </div>
    <div class="card-footer">
        <button>Add to Cart</button>
    </div>
</div>
```

**Multiple `<div>` Elements for Grid Layout:**
```html
<div class="container">
    <div class="row">
        <div class="column">
            <h3>Column 1</h3>
            <p>Content for first column</p>
        </div>
        <div class="column">
            <h3>Column 2</h3>
            <p>Content for second column</p>
        </div>
        <div class="column">
            <h3>Column 3</h3>
            <p>Content for third column</p>
        </div>
    </div>
</div>
```

##### The `<span>` Element (Inline Container)

The `<span>` element is a generic inline container used to group inline content for styling purposes. It doesn't start on a new line and only takes up as much width as necessary.

**Basic `<span>` Example:**
```html
<p>This is a <span>simple span</span> inside a paragraph.</p>
```

**Using `<span>` for Text Styling:**
```html
<p>The word <span style="color: red; font-weight: bold;">important</span> is highlighted in this sentence.</p>

<p>Price: <span style="font-size: 24px; color: green;">$19.99</span></p>

<p>Email us at <span style="font-family: monospace; background-color: #f0f0f0;">contact@example.com</span></p>
```

**Multiple `<span>` Elements in Text:**
```html
<p>
    This text contains <span style="color: blue;">blue text</span>,
    <span style="color: red;">red text</span>, and
    <span style="background-color: yellow;">highlighted text</span>.
</p>
```

**Using `<span>` with Classes:**
```html
<style>
    .highlight { background-color: yellow; }
    .bold-text { font-weight: bold; }
    .error { color: red; }
    .success { color: green; }
</style>

<p>Status: <span class="success">Completed successfully!</span></p>
<p>Error: <span class="error">Invalid input detected.</span></p>
<p>Note: <span class="highlight bold-text">This is very important!</span></p>
```

**`<span>` for Icons or Special Characters:**
```html
<p>
    <span style="font-size: 20px; color: gold;">★</span>
    Premium Member
</p>

<p>
    Temperature: <span style="color: red;">32°C</span>
    <span style="color: blue;">↑</span>
</p>
```

##### Difference Between `<div>` and `<span>`

| Feature | `<div>` | `<span>` |
|---------|---------|----------|
| Type | Block-level | Inline |
| Line Break | Starts on a new line | Does not start on a new line |
| Width | Takes full width available | Takes only necessary width |
| Use Case | Layout structure, grouping blocks | Styling parts of text |
| Can Contain | Block and inline elements | Only inline elements |

**Comparing `<div>` and `<span>` Side by Side:**
```html
<!-- Block-level div -->
<div style="background-color: lightblue; padding: 10px;">
    This is a div. It takes the full width.
</div>
<div style="background-color: lightgreen; padding: 10px;">
    This is another div. It starts on a new line.
</div>

<!-- Inline span -->
<p>
    <span style="background-color: lightblue; padding: 5px;">This is a span.</span>
    <span style="background-color: lightgreen; padding: 5px;">This is another span.</span>
    They appear on the same line.
</p>
```

**Practical Example - Combining `<div>` and `<span>`:**
```html
<div class="alert" style="background-color: #fff3cd; border: 1px solid #ffc107; padding: 15px;">
    <span style="font-weight: bold; color: #856404;">Warning:</span>
    <span>Please save your work before proceeding.</span>
</div>

<div class="article">
    <h2>Article Title</h2>
    <p>
        Published on <span class="date" style="font-style: italic;">January 15, 2024</span>
        by <span class="author" style="font-weight: bold;">John Doe</span>
    </p>
    <p>Article content goes here...</p>
</div>
```

## 🎯 Mini Task 1: HTML Basics Practice

**Task:** Create a simple HTML page about yourself with the following requirements:
1. Use proper HTML5 document structure (DOCTYPE, html, head, body)
2. Include a page title in the `<head>`
3. Add at least 3 different heading levels (h1, h2, h3)
4. Write 2-3 paragraphs about yourself using `<p>` tags
5. Use at least 3 different text formatting tags (bold, italic, mark, etc.)
6. Include a horizontal rule (`<hr>`) to separate sections
7. Add comments to explain different sections of your code

**Expected Outcome:** A well-structured personal profile page demonstrating basic HTML elements.

---

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

## 🎯 Mini Task 2: Working with Lists

**Task:** Create an HTML page for a recipe with the following:
1. Use an unordered list for ingredients
2. Use an ordered list for cooking steps
3. Create a nested list showing:
   - Different meal categories (breakfast, lunch, dinner)
   - Under each category, list 2-3 dish names
4. Use a definition list to define at least 3 cooking terms (e.g., "Sauté", "Blanch", "Julienne")

**Bonus Challenge:** Style the list markers using the `type` or `style` attributes.

**Expected Outcome:** A well-organized recipe page demonstrating all three types of lists.

---

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

## 🎯 Mini Task 4: Image Gallery with Imagemap

**Task:** Create an interactive image gallery:
1. Display at least 3 images with proper `alt` text
2. Set width and height attributes for each image
3. Create a client-side imagemap on one image with at least 3 clickable areas (use different shapes: rectangle, circle)
4. Each area should link to a different page or section
5. Add a `<figure>` element with a `<figcaption>` for at least one image

**Bonus Challenge:** Create one image as a server-side imagemap using the `ismap` attribute.

**Expected Outcome:** An image gallery with at least one interactive imagemap.

---

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

The `colspan` and `rowspan` attributes allow table cells to span across multiple columns or rows, creating more complex table layouts.

##### Column Spanning (`colspan`)

The `colspan` attribute specifies how many columns a cell should span.

**Basic `colspan` Example:**
```html
<table border="1" style="border-collapse: collapse;">
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

**`colspan` for Table Headers:**
```html
<table border="1" style="border-collapse: collapse; width: 100%;">
    <tr>
        <th colspan="3">Student Information</th>
    </tr>
    <tr>
        <th>Name</th>
        <th>Roll Number</th>
        <th>Grade</th>
    </tr>
    <tr>
        <td>John Doe</td>
        <td>101</td>
        <td>A</td>
    </tr>
    <tr>
        <td>Jane Smith</td>
        <td>102</td>
        <td>B+</td>
    </tr>
</table>
```

**Complex `colspan` Example - Timetable:**
```html
<table border="1" style="border-collapse: collapse; width: 100%;">
    <tr>
        <th>Day</th>
        <th>9:00-10:00</th>
        <th>10:00-11:00</th>
        <th>11:00-12:00</th>
        <th>12:00-1:00</th>
    </tr>
    <tr>
        <td>Monday</td>
        <td>Math</td>
        <td>English</td>
        <td colspan="2" style="text-align: center; background-color: #f0f0f0;">Lunch Break</td>
    </tr>
    <tr>
        <td>Tuesday</td>
        <td colspan="2" style="text-align: center; background-color: #e8f4f8;">Lab Session</td>
        <td>Science</td>
        <td>History</td>
    </tr>
    <tr>
        <td>Wednesday</td>
        <td>Physics</td>
        <td>Chemistry</td>
        <td>Biology</td>
        <td>Sports</td>
    </tr>
</table>
```

**Invoice Table with `colspan`:**
```html
<table border="1" style="border-collapse: collapse; width: 100%;">
    <tr style="background-color: #333; color: white;">
        <th colspan="3">Invoice #12345</th>
    </tr>
    <tr>
        <th>Item</th>
        <th>Quantity</th>
        <th>Price</th>
    </tr>
    <tr>
        <td>Product A</td>
        <td>2</td>
        <td>$20</td>
    </tr>
    <tr>
        <td>Product B</td>
        <td>1</td>
        <td>$15</td>
    </tr>
    <tr style="background-color: #f9f9f9;">
        <td colspan="2" style="text-align: right; font-weight: bold;">Total:</td>
        <td style="font-weight: bold;">$55</td>
    </tr>
</table>
```

##### Row Spanning (`rowspan`)

The `rowspan` attribute specifies how many rows a cell should span.

**Basic `rowspan` Example:**
```html
<table border="1" style="border-collapse: collapse;">
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

**`rowspan` for Contact Information:**
```html
<table border="1" style="border-collapse: collapse; width: 100%;">
    <tr>
        <th rowspan="3" style="vertical-align: middle; background-color: #e8f4f8;">Contact Details</th>
        <th>Email</th>
        <td>john@example.com</td>
    </tr>
    <tr>
        <th>Phone</th>
        <td>555-1234</td>
    </tr>
    <tr>
        <th>Address</th>
        <td>123 Main Street, City</td>
    </tr>
</table>
```

**Employee Table with `rowspan`:**
```html
<table border="1" style="border-collapse: collapse; width: 100%;">
    <tr>
        <th>Department</th>
        <th>Employee Name</th>
        <th>Position</th>
    </tr>
    <tr>
        <td rowspan="3" style="vertical-align: middle; background-color: #fff3cd;">IT Department</td>
        <td>John Doe</td>
        <td>Manager</td>
    </tr>
    <tr>
        <td>Jane Smith</td>
        <td>Developer</td>
    </tr>
    <tr>
        <td>Bob Johnson</td>
        <td>Designer</td>
    </tr>
    <tr>
        <td rowspan="2" style="vertical-align: middle; background-color: #d4edda;">HR Department</td>
        <td>Alice Brown</td>
        <td>HR Manager</td>
    </tr>
    <tr>
        <td>Charlie Wilson</td>
        <td>Recruiter</td>
    </tr>
</table>
```

##### Combining `colspan` and `rowspan`

You can use both attributes together to create complex table structures.

**Simple Combined Example:**
```html
<table border="1" style="border-collapse: collapse; width: 100%;">
    <tr>
        <th colspan="3" style="text-align: center; background-color: #333; color: white;">Product Comparison</th>
    </tr>
    <tr>
        <th>Feature</th>
        <th>Basic Plan</th>
        <th>Premium Plan</th>
    </tr>
    <tr>
        <td rowspan="2" style="vertical-align: middle; background-color: #f0f0f0;">Storage</td>
        <td>10 GB</td>
        <td>100 GB</td>
    </tr>
    <tr>
        <td colspan="2" style="text-align: center; background-color: #fff3cd;">Cloud Backup Included</td>
    </tr>
    <tr>
        <td>Support</td>
        <td>Email</td>
        <td>24/7 Phone + Email</td>
    </tr>
</table>
```

**Advanced Combined Example - Course Schedule:**
```html
<table border="1" style="border-collapse: collapse; width: 100%; text-align: center;">
    <tr style="background-color: #333; color: white;">
        <th colspan="5">Weekly Course Schedule</th>
    </tr>
    <tr style="background-color: #f0f0f0;">
        <th>Time</th>
        <th>Monday</th>
        <th>Tuesday</th>
        <th>Wednesday</th>
        <th>Thursday</th>
    </tr>
    <tr>
        <td>9:00-10:00</td>
        <td rowspan="2" style="vertical-align: middle; background-color: #e8f4f8;">Mathematics<br>(Room 101)</td>
        <td>English</td>
        <td>Science</td>
        <td>History</td>
    </tr>
    <tr>
        <td>10:00-11:00</td>
        <td>Physics</td>
        <td rowspan="2" style="vertical-align: middle; background-color: #fff3cd;">Computer Lab<br>(Lab 1)</td>
        <td>Chemistry</td>
    </tr>
    <tr>
        <td>11:00-12:00</td>
        <td>Biology</td>
        <td>Geography</td>
        <td>Physical Ed</td>
    </tr>
    <tr>
        <td>12:00-1:00</td>
        <td colspan="4" style="background-color: #d4edda;">Lunch Break</td>
    </tr>
    <tr>
        <td>1:00-2:00</td>
        <td colspan="2" style="background-color: #f8d7da;">Sports Activities</td>
        <td>Art</td>
        <td>Music</td>
    </tr>
</table>
```

**Complex Example - Project Timeline:**
```html
<table border="1" style="border-collapse: collapse; width: 100%;">
    <tr style="background-color: #333; color: white;">
        <th colspan="4">Project Timeline - Q1 2024</th>
    </tr>
    <tr style="background-color: #f0f0f0;">
        <th>Phase</th>
        <th>January</th>
        <th>February</th>
        <th>March</th>
    </tr>
    <tr>
        <td rowspan="2" style="vertical-align: middle; background-color: #e8f4f8; font-weight: bold;">Planning</td>
        <td>Requirements</td>
        <td colspan="2" style="text-align: center; background-color: #fff3cd;">Design & Prototyping</td>
    </tr>
    <tr>
        <td>Research</td>
        <td>Finalize Specs</td>
        <td>Review</td>
    </tr>
    <tr>
        <td rowspan="2" style="vertical-align: middle; background-color: #d4edda; font-weight: bold;">Development</td>
        <td colspan="3" style="text-align: center;">Backend Development</td>
    </tr>
    <tr>
        <td>-</td>
        <td colspan="2" style="text-align: center;">Frontend Development</td>
    </tr>
    <tr>
        <td style="background-color: #f8d7da; font-weight: bold;">Testing</td>
        <td>-</td>
        <td>-</td>
        <td>QA Testing</td>
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

#### Web Page Structure Using Tables

While tables were historically used for layout, modern web design uses CSS and `<div>` elements for layout instead. Tables should only be used for tabular data. However, understanding table-based layouts is important for maintaining legacy code and understanding web design history.

**Basic Two-Column Layout Using Tables:**
```html
<!DOCTYPE html>
<html>
<head>
    <title>Table-Based Layout</title>
</head>
<body>
    <table border="0" cellpadding="0" cellspacing="0" width="100%">
        <tr>
            <td width="25%" style="background-color: #f0f0f0; padding: 10px; vertical-align: top;">
                <h3>Navigation</h3>
                <ul>
                    <li><a href="#home">Home</a></li>
                    <li><a href="#about">About</a></li>
                    <li><a href="#services">Services</a></li>
                    <li><a href="#contact">Contact</a></li>
                </ul>
            </td>
            <td width="75%" style="padding: 10px; vertical-align: top;">
                <h1>Welcome to My Website</h1>
                <p>This is the main content area.</p>
                <p>Content goes here...</p>
            </td>
        </tr>
    </table>
</body>
</html>
```

**Complete Web Page Layout Using Tables:**
```html
<!DOCTYPE html>
<html>
<head>
    <title>Complete Table Layout</title>
    <style>
        body { margin: 0; padding: 0; font-family: Arial, sans-serif; }
        table { border-collapse: collapse; }
    </style>
</head>
<body>
    <!-- Main Container Table -->
    <table width="100%" border="0" cellpadding="0" cellspacing="0">
        <!-- Header Row -->
        <tr>
            <td colspan="3" style="background-color: #333; color: white; padding: 20px;">
                <h1 style="margin: 0;">My Website</h1>
                <p style="margin: 5px 0 0 0;">Welcome to our site</p>
            </td>
        </tr>

        <!-- Navigation Row -->
        <tr>
            <td colspan="3" style="background-color: #666; padding: 10px;">
                <a href="#home" style="color: white; margin-right: 15px; text-decoration: none;">Home</a>
                <a href="#about" style="color: white; margin-right: 15px; text-decoration: none;">About</a>
                <a href="#services" style="color: white; margin-right: 15px; text-decoration: none;">Services</a>
                <a href="#contact" style="color: white; text-decoration: none;">Contact</a>
            </td>
        </tr>

        <!-- Content Row with 3 columns -->
        <tr>
            <!-- Left Sidebar -->
            <td width="20%" style="background-color: #f5f5f5; padding: 15px; vertical-align: top;">
                <h3>Sidebar</h3>
                <ul style="list-style-type: none; padding: 0;">
                    <li style="margin-bottom: 10px;"><a href="#link1">Link 1</a></li>
                    <li style="margin-bottom: 10px;"><a href="#link2">Link 2</a></li>
                    <li style="margin-bottom: 10px;"><a href="#link3">Link 3</a></li>
                </ul>
            </td>

            <!-- Main Content -->
            <td width="60%" style="padding: 15px; vertical-align: top;">
                <h2>Main Content Area</h2>
                <p>This is the main content section where your primary information goes.</p>
                <p>You can add multiple paragraphs, images, and other content here.</p>

                <!-- Nested Table for Sub-content -->
                <table width="100%" border="1" style="border-collapse: collapse; margin-top: 20px;">
                    <tr style="background-color: #e0e0e0;">
                        <th style="padding: 10px;">Feature</th>
                        <th style="padding: 10px;">Description</th>
                    </tr>
                    <tr>
                        <td style="padding: 10px;">Feature 1</td>
                        <td style="padding: 10px;">Description of feature 1</td>
                    </tr>
                    <tr>
                        <td style="padding: 10px;">Feature 2</td>
                        <td style="padding: 10px;">Description of feature 2</td>
                    </tr>
                </table>
            </td>

            <!-- Right Sidebar -->
            <td width="20%" style="background-color: #f5f5f5; padding: 15px; vertical-align: top;">
                <h3>News</h3>
                <div style="background-color: white; padding: 10px; margin-bottom: 10px; border: 1px solid #ddd;">
                    <h4 style="margin: 0 0 5px 0;">Update 1</h4>
                    <p style="margin: 0; font-size: 12px;">Latest news item...</p>
                </div>
                <div style="background-color: white; padding: 10px; border: 1px solid #ddd;">
                    <h4 style="margin: 0 0 5px 0;">Update 2</h4>
                    <p style="margin: 0; font-size: 12px;">Another news item...</p>
                </div>
            </td>
        </tr>

        <!-- Footer Row -->
        <tr>
            <td colspan="3" style="background-color: #333; color: white; padding: 15px; text-align: center;">
                <p style="margin: 0;">&copy; 2024 My Website. All rights reserved.</p>
                <p style="margin: 5px 0 0 0; font-size: 12px;">
                    <a href="#privacy" style="color: #ccc; margin-right: 10px;">Privacy Policy</a>
                    <a href="#terms" style="color: #ccc;">Terms of Service</a>
                </p>
            </td>
        </tr>
    </table>
</body>
</html>
```

**Table-Based E-commerce Product Layout:**
```html
<!DOCTYPE html>
<html>
<head>
    <title>Product Page - Table Layout</title>
</head>
<body style="margin: 0; font-family: Arial, sans-serif;">
    <table width="100%" border="0" cellpadding="0" cellspacing="0">
        <!-- Header -->
        <tr>
            <td colspan="2" style="background-color: #4CAF50; color: white; padding: 20px;">
                <h1 style="margin: 0;">Online Store</h1>
            </td>
        </tr>

        <!-- Main Content Area -->
        <tr>
            <td width="70%" style="padding: 20px; vertical-align: top;">
                <h2>Product Name</h2>

                <!-- Product Details Table -->
                <table width="100%" border="0" cellpadding="10" cellspacing="0">
                    <tr>
                        <td width="40%" style="vertical-align: top;">
                            <div style="background-color: #f0f0f0; padding: 20px; text-align: center; border: 1px solid #ddd;">
                                [Product Image Here]
                                <br>400 x 400 px
                            </div>
                        </td>
                        <td width="60%" style="vertical-align: top; padding-left: 20px;">
                            <h3>Product Details</h3>
                            <p><strong>Price:</strong> <span style="color: #4CAF50; font-size: 24px;">$29.99</span></p>
                            <p><strong>Availability:</strong> In Stock</p>
                            <p><strong>Description:</strong><br>
                            This is a detailed description of the product. It includes all the important features and benefits that customers need to know.</p>
                            <button style="background-color: #4CAF50; color: white; padding: 12px 24px; border: none; cursor: pointer; font-size: 16px;">
                                Add to Cart
                            </button>
                        </td>
                    </tr>
                </table>

                <!-- Product Specifications -->
                <h3 style="margin-top: 30px;">Specifications</h3>
                <table width="100%" border="1" style="border-collapse: collapse;">
                    <tr style="background-color: #f0f0f0;">
                        <th style="padding: 10px; text-align: left;">Specification</th>
                        <th style="padding: 10px; text-align: left;">Details</th>
                    </tr>
                    <tr>
                        <td style="padding: 10px;">Brand</td>
                        <td style="padding: 10px;">Sample Brand</td>
                    </tr>
                    <tr>
                        <td style="padding: 10px;">Model</td>
                        <td style="padding: 10px;">XYZ-123</td>
                    </tr>
                    <tr>
                        <td style="padding: 10px;">Weight</td>
                        <td style="padding: 10px;">2.5 kg</td>
                    </tr>
                    <tr>
                        <td style="padding: 10px;">Dimensions</td>
                        <td style="padding: 10px;">30 x 20 x 10 cm</td>
                    </tr>
                </table>
            </td>

            <!-- Shopping Cart Sidebar -->
            <td width="30%" style="background-color: #f9f9f9; padding: 20px; vertical-align: top;">
                <h3>Your Cart</h3>
                <table width="100%" border="0" cellpadding="5" cellspacing="0" style="background-color: white; border: 1px solid #ddd;">
                    <tr style="background-color: #f0f0f0;">
                        <td colspan="2" style="padding: 10px;"><strong>Cart Items</strong></td>
                    </tr>
                    <tr>
                        <td style="padding: 10px;">Item 1</td>
                        <td style="padding: 10px; text-align: right;">$15.00</td>
                    </tr>
                    <tr>
                        <td style="padding: 10px;">Item 2</td>
                        <td style="padding: 10px; text-align: right;">$20.00</td>
                    </tr>
                    <tr style="background-color: #f0f0f0;">
                        <td style="padding: 10px;"><strong>Total</strong></td>
                        <td style="padding: 10px; text-align: right;"><strong>$35.00</strong></td>
                    </tr>
                </table>

                <h3 style="margin-top: 30px;">Related Products</h3>
                <table width="100%" border="0" cellpadding="0" cellspacing="0">
                    <tr>
                        <td style="background-color: white; border: 1px solid #ddd; padding: 10px; margin-bottom: 10px;">
                            <strong>Product 1</strong><br>
                            <span style="color: #4CAF50;">$19.99</span>
                        </td>
                    </tr>
                    <tr><td style="height: 10px;"></td></tr>
                    <tr>
                        <td style="background-color: white; border: 1px solid #ddd; padding: 10px;">
                            <strong>Product 2</strong><br>
                            <span style="color: #4CAF50;">$24.99</span>
                        </td>
                    </tr>
                </table>
            </td>
        </tr>

        <!-- Footer -->
        <tr>
            <td colspan="2" style="background-color: #333; color: white; padding: 20px; text-align: center;">
                <p style="margin: 0;">&copy; 2024 Online Store. All rights reserved.</p>
            </td>
        </tr>
    </table>
</body>
</html>
```

#### Web Page Structure Using Div Elements

Modern web development uses `<div>` elements with CSS for layout. This approach is more flexible, maintainable, and semantically correct than table-based layouts.

**Basic Two-Column Layout Using Divs:**
```html
<!DOCTYPE html>
<html>
<head>
    <title>Div-Based Layout</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            font-family: Arial, sans-serif;
        }
        .container {
            display: flex;
            min-height: 100vh;
        }
        .sidebar {
            width: 25%;
            background-color: #f0f0f0;
            padding: 20px;
        }
        .main-content {
            width: 75%;
            padding: 20px;
        }
        .sidebar ul {
            list-style-type: none;
            padding: 0;
        }
        .sidebar li {
            margin-bottom: 10px;
        }
        .sidebar a {
            text-decoration: none;
            color: #333;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="sidebar">
            <h3>Navigation</h3>
            <ul>
                <li><a href="#home">Home</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#services">Services</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
        </div>
        <div class="main-content">
            <h1>Welcome to My Website</h1>
            <p>This is the main content area.</p>
            <p>Content goes here...</p>
        </div>
    </div>
</body>
</html>
```

**Complete Web Page Layout Using Divs:**
```html
<!DOCTYPE html>
<html>
<head>
    <title>Modern Div Layout</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: Arial, sans-serif;
            line-height: 1.6;
        }

        /* Header Styles */
        .header {
            background-color: #333;
            color: white;
            padding: 20px;
        }

        .header h1 {
            margin-bottom: 5px;
        }

        /* Navigation Styles */
        .navbar {
            background-color: #666;
            padding: 10px 20px;
        }

        .navbar a {
            color: white;
            text-decoration: none;
            margin-right: 15px;
        }

        .navbar a:hover {
            color: #ddd;
        }

        /* Main Container with 3 columns */
        .main-container {
            display: flex;
            min-height: 500px;
        }

        /* Left Sidebar */
        .sidebar-left {
            width: 20%;
            background-color: #f5f5f5;
            padding: 15px;
        }

        .sidebar-left h3 {
            margin-bottom: 15px;
        }

        .sidebar-left ul {
            list-style-type: none;
        }

        .sidebar-left li {
            margin-bottom: 10px;
        }

        /* Main Content */
        .content {
            width: 60%;
            padding: 20px;
        }

        .content h2 {
            margin-bottom: 15px;
        }

        .content p {
            margin-bottom: 15px;
        }

        .feature-box {
            border: 1px solid #ddd;
            padding: 15px;
            margin-top: 20px;
            background-color: #fff;
        }

        .feature-box h3 {
            margin-bottom: 10px;
        }

        /* Right Sidebar */
        .sidebar-right {
            width: 20%;
            background-color: #f5f5f5;
            padding: 15px;
        }

        .news-item {
            background-color: white;
            padding: 10px;
            margin-bottom: 10px;
            border: 1px solid #ddd;
            border-radius: 4px;
        }

        .news-item h4 {
            margin-bottom: 5px;
        }

        .news-item p {
            font-size: 12px;
            color: #666;
        }

        /* Footer */
        .footer {
            background-color: #333;
            color: white;
            padding: 20px;
            text-align: center;
        }

        .footer p {
            margin-bottom: 5px;
        }

        .footer a {
            color: #ccc;
            margin: 0 10px;
            text-decoration: none;
        }
    </style>
</head>
<body>
    <!-- Header -->
    <div class="header">
        <h1>My Website</h1>
        <p>Welcome to our site</p>
    </div>

    <!-- Navigation -->
    <div class="navbar">
        <a href="#home">Home</a>
        <a href="#about">About</a>
        <a href="#services">Services</a>
        <a href="#contact">Contact</a>
    </div>

    <!-- Main Container -->
    <div class="main-container">
        <!-- Left Sidebar -->
        <div class="sidebar-left">
            <h3>Sidebar</h3>
            <ul>
                <li><a href="#link1">Link 1</a></li>
                <li><a href="#link2">Link 2</a></li>
                <li><a href="#link3">Link 3</a></li>
                <li><a href="#link4">Link 4</a></li>
            </ul>
        </div>

        <!-- Main Content -->
        <div class="content">
            <h2>Main Content Area</h2>
            <p>This is the main content section where your primary information goes.</p>
            <p>You can add multiple paragraphs, images, and other content here.</p>

            <div class="feature-box">
                <h3>Featured Content</h3>
                <p>This is a featured content section that stands out from the rest of the page.</p>
                <p>You can use this for important announcements, promotions, or highlighted information.</p>
            </div>

            <div class="feature-box">
                <h3>Another Section</h3>
                <p>Additional content can be organized in separate boxes like this.</p>
            </div>
        </div>

        <!-- Right Sidebar -->
        <div class="sidebar-right">
            <h3>News</h3>
            <div class="news-item">
                <h4>Update 1</h4>
                <p>Latest news item goes here...</p>
            </div>
            <div class="news-item">
                <h4>Update 2</h4>
                <p>Another news item goes here...</p>
            </div>
            <div class="news-item">
                <h4>Update 3</h4>
                <p>More news content here...</p>
            </div>
        </div>
    </div>

    <!-- Footer -->
    <div class="footer">
        <p>&copy; 2024 My Website. All rights reserved.</p>
        <p>
            <a href="#privacy">Privacy Policy</a>
            <a href="#terms">Terms of Service</a>
        </p>
    </div>
</body>
</html>
```

**Responsive Div-Based Layout (Mobile-Friendly):**
```html
<!DOCTYPE html>
<html>
<head>
    <title>Responsive Layout</title>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: Arial, sans-serif;
        }

        .header {
            background-color: #4CAF50;
            color: white;
            padding: 20px;
            text-align: center;
        }

        .navbar {
            background-color: #333;
            overflow: hidden;
        }

        .navbar a {
            float: left;
            display: block;
            color: white;
            text-align: center;
            padding: 14px 16px;
            text-decoration: none;
        }

        .navbar a:hover {
            background-color: #ddd;
            color: black;
        }

        .row {
            display: flex;
            flex-wrap: wrap;
        }

        .column {
            flex: 25%;
            padding: 15px;
        }

        .column.main {
            flex: 50%;
        }

        .card {
            background-color: white;
            padding: 20px;
            margin-bottom: 20px;
            border: 1px solid #ddd;
            border-radius: 4px;
        }

        .card h2 {
            margin-bottom: 10px;
        }

        .footer {
            background-color: #333;
            color: white;
            text-align: center;
            padding: 20px;
        }

        /* Responsive layout - makes the columns stack on top of each other on small screens */
        @media screen and (max-width: 768px) {
            .column {
                flex: 100%;
            }

            .navbar a {
                float: none;
                width: 100%;
            }
        }
    </style>
</head>
<body>
    <div class="header">
        <h1>Responsive Website</h1>
        <p>Resize the browser window to see the effect</p>
    </div>

    <div class="navbar">
        <a href="#home">Home</a>
        <a href="#about">About</a>
        <a href="#services">Services</a>
        <a href="#contact">Contact</a>
    </div>

    <div class="row">
        <div class="column">
            <div class="card">
                <h2>Sidebar</h2>
                <p>This is the sidebar content. It will stack on mobile devices.</p>
            </div>
        </div>

        <div class="column main">
            <div class="card">
                <h2>Main Content</h2>
                <p>This is the main content area. It takes up more space on larger screens.</p>
                <p>The layout automatically adjusts based on screen size.</p>
            </div>

            <div class="card">
                <h2>Another Section</h2>
                <p>Additional content goes here.</p>
            </div>
        </div>

        <div class="column">
            <div class="card">
                <h2>Right Column</h2>
                <p>This is the right column content.</p>
            </div>
        </div>
    </div>

    <div class="footer">
        <p>&copy; 2024 Responsive Website</p>
    </div>
</body>
</html>
```

**Div-Based Grid Layout (Modern Approach):**
```html
<!DOCTYPE html>
<html>
<head>
    <title>CSS Grid Layout</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: Arial, sans-serif;
        }

        .container {
            display: grid;
            grid-template-areas:
                "header header header"
                "nav nav nav"
                "sidebar main aside"
                "footer footer footer";
            grid-template-columns: 1fr 3fr 1fr;
            grid-template-rows: auto auto 1fr auto;
            min-height: 100vh;
            gap: 0;
        }

        .header {
            grid-area: header;
            background-color: #333;
            color: white;
            padding: 20px;
        }

        .navbar {
            grid-area: nav;
            background-color: #666;
            padding: 10px 20px;
        }

        .navbar a {
            color: white;
            text-decoration: none;
            margin-right: 15px;
        }

        .sidebar {
            grid-area: sidebar;
            background-color: #f5f5f5;
            padding: 20px;
        }

        .main-content {
            grid-area: main;
            padding: 20px;
        }

        .aside {
            grid-area: aside;
            background-color: #f5f5f5;
            padding: 20px;
        }

        .footer {
            grid-area: footer;
            background-color: #333;
            color: white;
            padding: 20px;
            text-align: center;
        }

        .content-box {
            background-color: #fff;
            border: 1px solid #ddd;
            padding: 15px;
            margin-bottom: 15px;
            border-radius: 4px;
        }

        /* Responsive: Stack on small screens */
        @media screen and (max-width: 768px) {
            .container {
                grid-template-areas:
                    "header"
                    "nav"
                    "main"
                    "sidebar"
                    "aside"
                    "footer";
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>CSS Grid Layout</h1>
            <p>Modern web page structure using CSS Grid</p>
        </div>

        <div class="navbar">
            <a href="#home">Home</a>
            <a href="#about">About</a>
            <a href="#services">Services</a>
            <a href="#contact">Contact</a>
        </div>

        <div class="sidebar">
            <h3>Menu</h3>
            <div class="content-box">
                <h4>Category 1</h4>
                <ul>
                    <li><a href="#item1">Item 1</a></li>
                    <li><a href="#item2">Item 2</a></li>
                </ul>
            </div>
        </div>

        <div class="main-content">
            <h2>Main Content</h2>
            <div class="content-box">
                <h3>Article Title</h3>
                <p>This is the main content area using CSS Grid layout.</p>
                <p>Grid layout provides a powerful way to create complex layouts with clean code.</p>
            </div>

            <div class="content-box">
                <h3>Another Article</h3>
                <p>More content goes here.</p>
            </div>
        </div>

        <div class="aside">
            <h3>Sidebar</h3>
            <div class="content-box">
                <h4>Quick Links</h4>
                <p>Important links and information</p>
            </div>
        </div>

        <div class="footer">
            <p>&copy; 2024 CSS Grid Layout Example</p>
        </div>
    </div>
</body>
</html>
```

**Comparison: Tables vs. Divs for Layout**

| Aspect | Table Layout | Div Layout |
|--------|-------------|------------|
| Semantic HTML | ❌ Not semantic (tables are for data) | ✅ Semantic and meaningful |
| Flexibility | ❌ Rigid structure | ✅ Highly flexible |
| Responsiveness | ❌ Difficult to make responsive | ✅ Easy to make responsive |
| Maintenance | ❌ Harder to maintain | ✅ Easier to maintain |
| Accessibility | ❌ Poor accessibility | ✅ Better accessibility |
| Modern Standard | ❌ Deprecated for layout | ✅ Current best practice |
| CSS Support | ❌ Limited styling options | ✅ Full CSS capabilities |
| Load Time | ❌ Can be slower | ✅ Generally faster |

**Best Practices:**
- Use `<table>` only for tabular data (actual data tables, spreadsheets, etc.)
- Use `<div>` elements with CSS (Flexbox, Grid) for page layout
- Always consider mobile responsiveness
- Use semantic HTML5 elements (`<header>`, `<nav>`, `<main>`, `<aside>`, `<footer>`) instead of generic divs when possible

## 🎯 Mini Task 5: Creating Data Tables

**Task:** Create a student grade report table:
1. Create a table with the following columns: Student Name, Subject, Midterm Score, Final Score, Total
2. Include at least 5 rows of student data
3. Add a `<caption>` describing the table
4. Use `<thead>`, `<tbody>`, and `<tfoot>` to structure the table
5. In the footer, show the average scores
6. Use `colspan` to merge cells in the header or footer
7. Use `rowspan` for at least one cell
8. Style the table with:
   - Borders using inline CSS
   - Different background colors for header and footer
   - Padding for cells
   - Alternating row colors using `nth-child` or inline styles

**Expected Outcome:** A professional-looking data table with proper structure and styling.

---

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

## 🎯 Mini Task 6: Building Interactive Forms

**Task:** Create a student registration form with the following fields:
1. Text inputs: First Name, Last Name, Email
2. Password field for creating a password
3. Radio buttons for Gender (Male, Female, Other)
4. Checkboxes for selecting interests (at least 4 options)
5. Dropdown select for choosing a course/major
6. Textarea for "Why do you want to join?"
7. File upload for profile picture
8. Number input for age (with min and max validation)
9. Date input for date of birth
10. Submit and Reset buttons

**Requirements:**
- Use `<fieldset>` and `<legend>` to group related fields
- Add `<label>` elements for all inputs (use the `for` attribute)
- Make at least 3 fields required
- Use placeholder text where appropriate
- Add a hidden field with a session ID (value: "12345")

**Bonus Challenge:** Add JavaScript validation to check if email is in correct format before submission.

**Expected Outcome:** A complete, well-organized registration form demonstrating various input types.

---

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
    <link rel="stylesheet" type="theme.css">
</head>
```

## 🎯 Mini Task 7: CSS Styling Methods

**Task:** Take the student registration form you created in Mini Task 6 and style it using all three CSS methods:

1. **Create an external CSS file (styles.css):**
   - Set body font-family and background color
   - Style all labels with a specific color and font-weight
   - Add margin and padding to form elements
   - Style the submit button with colors and hover effects

2. **Add internal CSS in the `<style>` tag:**
   - Style the fieldset with border and background
   - Add styling for input focus states
   - Create styles for error messages (even if not displayed yet)

3. **Use inline CSS for:**
   - Making one specific heading a unique color
   - Adding a special style to the submit button that overrides other styles

4. **Additional Requirements:**
   - Ensure the form is centered on the page
   - Add box shadows to input fields
   - Create a color scheme that's visually appealing
   - Make sure text is readable with good contrast

**Expected Outcome:** A beautifully styled registration form demonstrating the CSS cascade and all three methods of applying styles.

---

**End of HTML and CSS Notes**
