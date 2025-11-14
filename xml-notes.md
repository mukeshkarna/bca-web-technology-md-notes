# XML Technologies: Student Notes

## Unit 3: The Client Tier (10 Hours)

*Notes based on curriculum topics covering XML and related technologies*

### Introduction to XML

XML (eXtensible Markup Language) is a markup language designed to store and transport data in a format that is both human-readable and machine-readable. Unlike HTML, which focuses on how data looks, XML focuses on what data is.

**Key Characteristics:**
- Self-descriptive
- Platform independent
- Extensible (create your own tags)
- Separates data from presentation
- Supports Unicode for international characters
- Hierarchical structure (tree-like)

**Basic XML Example:**
```xml
<?xml version="1.0" encoding="UTF-8"?>
<students>
  <student id="101">
    <name>John Smith</name>
    <major>Computer Science</major>
    <year>2</year>
  </student>
  <student id="102">
    <name>Emily Johnson</name>
    <major>Mathematics</major>
    <year>3</year>
  </student>
</students>
```

### Elements and Attributes

**Elements** are the basic building blocks of XML. An element consists of a start tag, content, and an end tag.

**Attributes** provide additional information about elements. They are always specified in the start tag and come in name/value pairs.

**Example showing both:**
```xml
<book category="fiction" format="hardcover">
  <title>The Great Gatsby</title>
  <author>F. Scott Fitzgerald</author>
  <year>1925</year>
  <price currency="USD">24.99</price>
</book>
```

In this example:
- `book`, `title`, `author`, `year`, and `price` are elements
- `category`, `format`, and `currency` are attributes

### Rules for Writing XML

1. **All XML documents must have a root element**
2. **XML tags are case sensitive** (`<name>` and `<Name>` are different)
3. **All XML elements must be closed** (either `<tag></tag>` or self-closing `<tag/>`)
4. **XML elements must be properly nested**
   ```xml
   <!-- Correct -->
   <outer><inner>Content</inner></outer>
   
   <!-- Incorrect -->
   <outer><inner>Content</outer></inner>
   ```
5. **Attribute values must be quoted**
   ```xml
   <element attribute="value">content</element>
   ```
6. **Special characters must be escaped**
   - `&lt;` for `<`
   - `&gt;` for `>`
   - `&amp;` for `&`
   - `&apos;` for `'`
   - `&quot;` for `"`
7. **Comments are written like HTML comments**
   ```xml
   <!-- This is a comment -->
   ```
8. **White space is preserved**

## 🎯 Mini Task 1: Creating Your First XML Document

**Task:** Create a well-formed XML document for a "Book Library":

1. **Create `library.xml` with:**
   - XML declaration with version and encoding
   - Root element `<library>`
   - At least 5 `<book>` elements as children

2. **Each book should have:**
   - `id` attribute (unique identifier)
   - `category` attribute (fiction/non-fiction/science/history)
   - Child elements: `<title>`, `<author>`, `<year>`, `<price>`, `<publisher>`
   - At least one book with multiple `<author>` elements

3. **Include special characters:**
   - Use entities like `&amp;`, `&lt;`, `&gt;` in at least one element
   - Add XML comments explaining different sections

4. **Validate your document:**
   - Ensure all tags are properly closed
   - Check that tags are properly nested
   - Verify all attribute values are quoted

**Expected Outcome:** A well-formed XML document representing a book library that follows all XML syntax rules.

---

### Namespaces

XML namespaces help avoid element name conflicts when combining XML documents from different vocabularies.

**Syntax:**
```xml
<prefix:element xmlns:prefix="URI">
```

**Example:**
```xml
<?xml version="1.0" encoding="UTF-8"?>
<root>
  <h:table xmlns:h="http://www.w3.org/TR/html4/">
    <h:tr>
      <h:td>HTML-style table</h:td>
    </h:tr>
  </h:table>
  
  <f:table xmlns:f="http://www.furniture.org/">
    <f:name>Coffee Table</f:name>
    <f:width>80</f:width>
    <f:length>120</f:length>
  </f:table>
</root>
```

## 🎯 Mini Task 2: Working with XML Namespaces

**Task:** Create a document combining multiple XML vocabularies using namespaces:

1. **Create `product-catalog.xml` with:**
   - Two namespaces: one for product info, one for HTML formatting
   - Namespace prefixes: `prod` for products, `html` for HTML elements

2. **Document structure:**
   ```xml
   <catalog xmlns:prod="http://example.com/products"
            xmlns:html="http://www.w3.org/1999/xhtml">
   ```

3. **Include:**
   - At least 3 products with `prod:` prefixed elements
   - HTML formatted descriptions using `html:` prefixed elements (p, strong, em)
   - Show how namespaces prevent element name conflicts

4. **Bonus:** Add a third namespace for pricing with currency conversions.

**Expected Outcome:** An XML document demonstrating proper use of namespaces to combine different XML vocabularies.

---

### XML Schema (XSD)

XML Schema Definition (XSD) defines the structure, content, and semantics of XML documents. It's more powerful than DTD and written in XML syntax itself.

**Simple Types and Complex Types:**

- **Simple Types**: Elements that contain only text (no child elements)
- **Complex Types**: Elements that contain child elements or attributes

**Example of XSD:**
```xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">

  <xs:element name="student">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="name" type="xs:string"/>
        <xs:element name="age" type="xs:positiveInteger"/>
        <xs:element name="email" type="emailType"/>
        <xs:element name="courses" type="coursesType"/>
      </xs:sequence>
      <xs:attribute name="id" type="xs:ID" use="required"/>
    </xs:complexType>
  </xs:element>
  
  <!-- Custom simple type with pattern restriction -->
  <xs:simpleType name="emailType">
    <xs:restriction base="xs:string">
      <xs:pattern value="[^@]+@[^\.]+\..+"/>
    </xs:restriction>
  </xs:simpleType>
  
  <!-- Complex type definition -->
  <xs:complexType name="coursesType">
    <xs:sequence>
      <xs:element name="course" maxOccurs="unbounded">
        <xs:complexType>
          <xs:sequence>
            <xs:element name="code" type="xs:string"/>
            <xs:element name="title" type="xs:string"/>
            <xs:element name="credits" type="xs:integer"/>
          </xs:sequence>
        </xs:complexType>
      </xs:element>
    </xs:sequence>
  </xs:complexType>
  
</xs:schema>
```

## 🎯 Mini Task 3: Creating an XML Schema (XSD)

**Task:** Create an XSD schema for the library.xml from Mini Task 1:

1. **Create `library.xsd` with:**
   - Proper XSD namespace declaration
   - Root element definition for `<library>`
   - Complex type definition for `<book>` element

2. **Define constraints:**
   - `id` attribute as required, type xs:ID
   - `category` as enumeration (fiction, non-fiction, science, history)
   - `year` as xs:integer with min=1000, max=current year
   - `price` as xs:decimal with 2 decimal places
   - `title` and `author` as required strings
   - `publisher` as optional string

3. **Advanced requirements:**
   - Allow 1-5 authors per book (using minOccurs and maxOccurs)
   - Create a custom simpleType for ISBN with pattern validation
   - Add email type for author contact with pattern restriction

4. **Validate:**
   - Link your library.xml to this schema
   - Test with valid and invalid data

**Expected Outcome:** A complete XSD schema that properly validates your XML library document.

---

### XSD Attributes

Attributes in XSD can have various properties:

- **use**: Specifies if an attribute is required or optional
  - `use="required"` - Must be included
  - `use="optional"` - Can be omitted (default)
  - `use="prohibited"` - Must not be included

- **default**: Specifies default value if attribute is omitted
  
- **fixed**: Specifies a fixed value (cannot be changed)

**Example:**
```xml
<xs:attribute name="status" type="xs:string" default="active"/>
<xs:attribute name="version" type="xs:string" fixed="1.0"/>
<xs:attribute name="id" type="xs:ID" use="required"/>
```

### Facets, Patterns, and Indicators

**Facets** restrict values of simple types:

```xml
<!-- String with length between 5 and 10 characters -->
<xs:simpleType name="username">
  <xs:restriction base="xs:string">
    <xs:minLength value="5"/>
    <xs:maxLength value="10"/>
  </xs:restriction>
</xs:simpleType>

<!-- Integer between 1 and 100 -->
<xs:simpleType name="score">
  <xs:restriction base="xs:integer">
    <xs:minInclusive value="1"/>
    <xs:maxInclusive value="100"/>
  </xs:restriction>
</xs:simpleType>
```

**Patterns** define specific formats using regular expressions:

```xml
<!-- US phone number format -->
<xs:simpleType name="usPhoneNumber">
  <xs:restriction base="xs:string">
    <xs:pattern value="\d{3}-\d{3}-\d{4}"/>
  </xs:restriction>
</xs:simpleType>
```

**Order Indicators** specify the order of elements:

- **All**: Child elements can appear in any order (each child occurs 0 or 1 time)
- **Choice**: Only one child element can appear
- **Sequence**: Child elements must appear in the specified order

**Example:**
```xml
<!-- All indicator -->
<xs:element name="person">
  <xs:complexType>
    <xs:all>
      <xs:element name="name" type="xs:string"/>
      <xs:element name="age" type="xs:integer" minOccurs="0"/>
      <xs:element name="email" type="xs:string" minOccurs="0"/>
    </xs:all>
  </xs:complexType>
</xs:element>

<!-- Choice indicator -->
<xs:element name="payment">
  <xs:complexType>
    <xs:choice>
      <xs:element name="cash" type="xs:decimal"/>
      <xs:element name="credit" type="creditCardType"/>
      <xs:element name="debit" type="debitCardType"/>
    </xs:choice>
  </xs:complexType>
</xs:element>

<!-- Sequence indicator -->
<xs:element name="address">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="street" type="xs:string"/>
      <xs:element name="city" type="xs:string"/>
      <xs:element name="state" type="xs:string"/>
      <xs:element name="zip" type="xs:string"/>
    </xs:sequence>
  </xs:complexType>
</xs:element>
```

**Occurrence Indicators** specify how many times an element can occur:

- **maxOccurs**: Maximum number of times an element can occur
- **minOccurs**: Minimum number of times an element can occur

```xml
<!-- Element that must appear at least once and at most 5 times -->
<xs:element name="author" type="xs:string" minOccurs="1" maxOccurs="5"/>

<!-- Element that can appear any number of times (including zero) -->
<xs:element name="comment" type="xs:string" minOccurs="0" maxOccurs="unbounded"/>
```

## 🎯 Mini Task 4: XSD Facets and Patterns

**Task:** Create an XSD for a "Student Registration System" demonstrating various facets and patterns:

1. **Create `student.xsd` with custom simpleTypes:**
   - **StudentID**: Pattern like "STU[0-9]{6}" (e.g., STU123456)
   - **Email**: Pattern for valid email format
   - **Age**: Integer with minInclusive=16, maxInclusive=100
   - **GPA**: Decimal with totalDigits=3, fractionDigits=2, range 0.00-4.00
   - **PhoneNumber**: Pattern for format (XXX) XXX-XXXX
   - **ZipCode**: Pattern for 5 or 9 digit ZIP codes

2. **Create complexType for Student with:**
   - Sequence of elements: firstName, lastName, email, age, gpa, phone
   - Attributes: studentID (required), enrollmentYear (fixed to current year)
   - Choice element for major (from enumerated list)

3. **Use indicators:**
   - `<xs:all>` for address elements (street, city, state, zip in any order)
   - `<xs:choice>` for contact preference (email, phone, or mail)
   - `<xs:sequence>` with minOccurs/maxOccurs for course enrollments (1-7 courses)

**Expected Outcome:** An XSD demonstrating mastery of patterns, facets, and occurrence indicators.

---

### Document Type Definition (DTD)

DTD provides a way to define the structure of an XML document. It's older than XSD but still widely used.

**Internal DTD Declaration:**
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE note [
  <!ELEMENT note (to, from, heading, body)>
  <!ELEMENT to (#PCDATA)>
  <!ELEMENT from (#PCDATA)>
  <!ELEMENT heading (#PCDATA)>
  <!ELEMENT body (#PCDATA)>
]>
<note>
  <to>John</to>
  <from>Jane</from>
  <heading>Reminder</heading>
  <body>Don't forget our meeting!</body>
</note>
```

**External DTD Declaration - Private:**
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE note SYSTEM "note.dtd">
<note>
  <to>John</to>
  <from>Jane</from>
  <heading>Reminder</heading>
  <body>Don't forget our meeting!</body>
</note>
```

**External DTD Declaration - Public:**
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
  <head>
    <title>Title</title>
  </head>
  <body>
    Content
  </body>
</html>
```

**Defining Elements and Attributes in DTD:**

```dtd
<!-- Element with specified children -->
<!ELEMENT book (title, author, year, publisher?)>

<!-- Element with any content -->
<!ELEMENT description ANY>

<!-- Element with text only -->
<!ELEMENT title (#PCDATA)>

<!-- Empty element -->
<!ELEMENT image EMPTY>

<!-- Mixed content element -->
<!ELEMENT paragraph (#PCDATA | emphasis | strong)*>

<!-- Attribute definitions -->
<!ATTLIST book
  id ID #REQUIRED
  category (fiction|non-fiction) "fiction"
  in-stock CDATA #IMPLIED
  lang NMTOKEN #FIXED "en"
>
```

## 🎯 Mini Task 5: Document Type Definition (DTD)

**Task:** Create both internal and external DTDs for a "Recipe Collection":

**Part 1: Internal DTD**
1. Create `recipes-internal.xml` with embedded DTD that defines:
   - Root element `<cookbook>`
   - `<recipe>` elements with attributes: id, category, difficulty
   - Child elements: `<name>`, `<prepTime>`, `<cookTime>`, `<servings>`
   - `<ingredients>` containing multiple `<ingredient>` with amount attribute
   - `<instructions>` containing multiple `<step>` elements

**Part 2: External DTD**
1. Create `recipes.dtd` (external file) with same definitions
2. Create `recipes-external.xml` that references this DTD using SYSTEM
3. Add entity definitions for common ingredients:
   ```dtd
   <!ENTITY salt "1 tsp salt">
   <!ENTITY pepper "1/2 tsp black pepper">
   ```

**Part 3: DTD Features**
- Use #PCDATA for text content
- Use #REQUIRED and #IMPLIED for attributes
- Use #FIXED for version attribute
- Create enumerated attribute type for difficulty (easy|medium|hard)
- Use (element1 | element2)* for choice elements

**Expected Outcome:** Two XML files (one with internal DTD, one with external) both validating correctly.

---

### XSL/XSLT

XSLT (eXtensible Stylesheet Language Transformations) is used to transform XML documents into other formats like HTML, XML, text, etc.

**Basic XSLT Example (transform XML to HTML):**

XML File (books.xml):
```xml
<?xml version="1.0" encoding="UTF-8"?>
<bookstore>
  <book category="fiction">
    <title>Harry Potter</title>
    <author>J.K. Rowling</author>
    <price>29.99</price>
  </book>
  <book category="non-fiction">
    <title>Steve Jobs</title>
    <author>Walter Isaacson</author>
    <price>19.99</price>
  </book>
</bookstore>
```

XSLT File (books.xsl):
```xml
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  
  <xsl:template match="/">
    <html>
      <head>
        <title>My Book Collection</title>
      </head>
      <body>
        <h1>My Books</h1>
        <table border="1">
          <tr bgcolor="#9acd32">
            <th>Title</th>
            <th>Author</th>
            <th>Price</th>
            <th>Category</th>
          </tr>
          <xsl:for-each select="bookstore/book">
            <tr>
              <td><xsl:value-of select="title"/></td>
              <td><xsl:value-of select="author"/></td>
              <td>$<xsl:value-of select="price"/></td>
              <td><xsl:value-of select="@category"/></td>
            </tr>
          </xsl:for-each>
        </table>
      </body>
    </html>
  </xsl:template>
  
</xsl:stylesheet>
```

**Key XSLT Elements:**

- `<xsl:template>` - Defines rules for transforming elements
- `<xsl:value-of>` - Extracts value of selected node
- `<xsl:for-each>` - Loops through selected nodes
- `<xsl:if>` - Conditional testing
- `<xsl:choose>`, `<xsl:when>`, `<xsl:otherwise>` - Multiple conditional testing
- `<xsl:sort>` - Sorts the output
- `<xsl:apply-templates>` - Applies templates to nodes

## 🎯 Mini Task 6: XSLT Transformation

**Task:** Transform the library.xml into an HTML page using XSLT:

1. **Create `library.xsl` that transforms library.xml into HTML:**
   - HTML page with proper structure (html, head, body)
   - Page title: "My Book Library"
   - CSS styling in the head section

2. **XSLT Requirements:**
   - Use `<xsl:template match="/">` for root template
   - Create an HTML table with headers: Title, Author, Year, Price, Category
   - Use `<xsl:for-each>` to iterate through all books
   - Use `<xsl:value-of>` to extract element values and attributes
   - Use `<xsl:sort>` to sort books by title

3. **Advanced Features:**
   - Use `<xsl:if>` to highlight books published after 2000 (different background color)
   - Use `<xsl:choose>`/`<xsl:when>`/`<xsl:otherwise>` to categorize prices:
     - Budget: < $15 (green)
     - Medium: $15-$30 (yellow)
     - Premium: > $30 (red)
   - Add a total count of books using `count()`
   - Format prices to 2 decimal places

4. **Apply the transformation:**
   - Link the XSL file in your XML
   - Open in browser or use XSLT processor

**Expected Outcome:** A styled HTML page generated from XML showing all books in a formatted table.

---

### XPath

XPath is a query language used to navigate through elements and attributes in an XML document. It's used by XSLT and other XML processing technologies.

**Basic XPath Expressions:**

- `/bookstore` - Selects the root element
- `/bookstore/book` - Selects all book elements under bookstore
- `//book` - Selects all book elements regardless of position
- `/bookstore/book[1]` - Selects the first book element
- `/bookstore/book[last()]` - Selects the last book element
- `/bookstore/book[position()<3]` - Selects the first two book elements
- `/bookstore/book[@category="fiction"]` - Selects books with category attribute "fiction"
- `/bookstore/book[price>20]` - Selects books with price greater than 20
- `/bookstore/book/title | /bookstore/book/author` - Selects all title and author elements

**Example using XPath in XSLT:**
```xml
<xsl:template match="/">
  <h2>Fiction Books:</h2>
  <ul>
    <xsl:for-each select="//book[@category='fiction']">
      <li><xsl:value-of select="title"/> by <xsl:value-of select="author"/></li>
    </xsl:for-each>
  </ul>
</xsl:template>
```

## 🎯 Mini Task 7: XPath Queries

**Task:** Practice XPath expressions using your library.xml:

Write XPath expressions to select:

1. **Basic Selection:**
   - All book titles
   - All authors
   - The root element
   - All book elements

2. **Attribute Selection:**
   - Books with category="fiction"
   - The id attribute of all books
   - Books where category is not "fiction"

3. **Positional Selection:**
   - The first book
   - The last book
   - The first 3 books
   - Every other book (odd positions)

4. **Conditional Selection:**
   - Books published after 2010
   - Books with price less than $20
   - Books with price between $15 and $30
   - Fiction books published after 2015

5. **Advanced XPath:**
   - All books by a specific author (use contains())
   - Books with titles starting with "The"
   - Count total number of books
   - Sum of all book prices
   - Average price of all books
   - Books that have multiple authors

**Testing:** Use an online XPath tester or browser console to verify each expression.

**Expected Outcome:** A document listing all XPath expressions with their results and explanations.

---

### XQuery

XQuery is a language designed for querying XML data. It extends XPath and adds programming features like functions, loops, and conditionals.

**Basic XQuery Example:**
```xquery
for $book in doc("books.xml")//book
where $book/price > 20
order by $book/title
return
  <expensive-book>
    <title>{$book/title/text()}</title>
    <price>{$book/price/text()}</price>
  </expensive-book>
```

**FLWOR expressions in XQuery:**
- **for**: Selects sequence of nodes
- **let**: Assigns values to variables
- **where**: Filters the nodes
- **order by**: Sorts the nodes
- **return**: Specifies the return value

**Complex XQuery Example:**
```xquery
let $fiction_count := count(doc("books.xml")//book[@category="fiction"])
let $nonfiction_count := count(doc("books.xml")//book[@category="non-fiction"])
return 
  <summary>
    <fiction-books>{$fiction_count}</fiction-books>
    <nonfiction-books>{$nonfiction_count}</nonfiction-books>
    <total-books>{$fiction_count + $nonfiction_count}</total-books>
  </summary>
```

## 🎯 Mini Task 8: XQuery Practice

**Task:** Write XQuery expressions for the library.xml:

1. **Basic FLWOR Expression:**
   ```xquery
   for $book in doc("library.xml")//book
   where $book/price > 20
   order by $book/title
   return $book/title
   ```
   Modify this to return complete book information as XML elements.

2. **Queries to Write:**

   a) **Filter and Sort:**
   - Find all fiction books, ordered by year (newest first)
   - Return title, author, and year in new XML structure

   b) **Grouping:**
   - Group books by category
   - Count books in each category
   - Return category name and count

   c) **Calculations:**
   - Calculate average price per category
   - Find the most expensive book in each category
   - Calculate total value of entire library

   d) **Complex Query:**
   - Create a report showing:
     - Total number of books
     - Number of books per category
     - Price statistics (min, max, average)
     - Books published in last 5 years

3. **Using let:**
   ```xquery
   let $total := sum(doc("library.xml")//price)
   let $count := count(doc("library.xml")//book)
   return <average>{$total div $count}</average>
   ```

**Expected Outcome:** A collection of working XQuery expressions with their results, demonstrating FLWOR operations.

---

### SAX and DOM

#### SAX (Simple API for XML)

SAX is an event-based API for parsing XML documents sequentially, reporting parsing events like the start and end of elements.

**Characteristics of SAX:**
- Memory efficient (doesn't load entire document)
- Fast for large documents
- Read-only (cannot modify the document)
- Sequential access (cannot navigate back)
- Good for streaming applications

**Java SAX Parser Example:**
```java
import org.xml.sax.*;
import org.xml.sax.helpers.*;
import javax.xml.parsers.*;
import java.io.*;

public class SAXExample {
    public static void main(String[] args) {
        try {
            // Create SAX parser factory
            SAXParserFactory factory = SAXParserFactory.newInstance();
            SAXParser saxParser = factory.newSAXParser();
            
            // Create handler
            DefaultHandler handler = new DefaultHandler() {
                boolean title = false;
                boolean author = false;
                
                // Event handlers
                public void startElement(String uri, String localName, String qName, Attributes attributes) {
                    if (qName.equalsIgnoreCase("title")) {
                        title = true;
                    }
                    if (qName.equalsIgnoreCase("author")) {
                        author = true;
                    }
                }
                
                public void endElement(String uri, String localName, String qName) {
                    // Reset flags when element ends
                    if (qName.equalsIgnoreCase("title")) {
                        title = false;
                    }
                    if (qName.equalsIgnoreCase("author")) {
                        author = false;
                    }
                }
                
                public void characters(char[] ch, int start, int length) {
                    if (title) {
                        System.out.println("Title: " + new String(ch, start, length));
                    }
                    if (author) {
                        System.out.println("Author: " + new String(ch, start, length));
                    }
                }
            };
            
            // Parse the file
            saxParser.parse("books.xml", handler);
            
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

#### DOM (Document Object Model)

DOM is a tree-based API that represents an XML document as a tree structure in memory.

**Characteristics of DOM:**
- Loads entire document into memory
- Can navigate in any direction
- Can modify the document
- More memory intensive
- Good for small to medium documents
- Better for complex operations

**Java DOM Parser Example:**
```java
import javax.xml.parsers.*;
import org.w3c.dom.*;
import java.io.*;

public class DOMExample {
    public static void main(String[] args) {
        try {
            // Create DOM parser factory
            DocumentBuilderFactory factory = DocumentBuilderFactory.newInstance();
            DocumentBuilder builder = factory.newDocumentBuilder();
            
            // Parse the file
            Document document = builder.parse(new File("books.xml"));
            
            // Normalize the document
            document.getDocumentElement().normalize();
            
            // Get all book elements
            NodeList bookList = document.getElementsByTagName("book");
            
            // Process each book
            for (int i = 0; i < bookList.getLength(); i++) {
                Node book = bookList.item(i);
                
                if (book.getNodeType() == Node.ELEMENT_NODE) {
                    Element bookElement = (Element) book;
                    
                    // Get category attribute
                    String category = bookElement.getAttribute("category");
                    
                    // Get title and author elements
                    String title = bookElement.getElementsByTagName("title").item(0).getTextContent();
                    String author = bookElement.getElementsByTagName("author").item(0).getTextContent();
                    
                    // Print information
                    System.out.println("Book " + (i+1) + ":");
                    System.out.println("  Category: " + category);
                    System.out.println("  Title: " + title);
                    System.out.println("  Author: " + author);
                }
            }
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

## 🎯 Mini Task 9: SAX vs DOM Parser Comparison

**Task:** Implement both SAX and DOM parsers for your library.xml:

**Part 1: SAX Parser (Event-Based)**

Create a program (Java, Python, or JavaScript) that:
1. Parses library.xml using SAX
2. Implements event handlers:
   - `startElement`: Track when entering each element
   - `endElement`: Track when leaving each element
   - `characters`: Capture text content
3. Extracts and prints:
   - All book titles
   - Count of total books
   - All books in "fiction" category
4. Measures memory usage and parsing time

**Part 2: DOM Parser (Tree-Based)**

Create a program that:
1. Parses library.xml using DOM
2. Loads entire document into memory as tree
3. Navigates the tree to:
   - Find and print all book titles
   - Count total books
   - Filter fiction books
   - Modify a book's price (update XML)
   - Add a new book element
   - Save modified XML back to file
4. Measures memory usage and parsing time

**Part 3: Comparison Analysis**

Create a comparison table:
| Feature | SAX | DOM |
|---------|-----|-----|
| Memory Usage | | |
| Parsing Speed | | |
| Can Modify | | |
| Can Navigate Back | | |
| Best Use Case | | |

**Expected Outcome:** Two working parsers with performance comparison showing when to use each approach.

---

### Creating XML Parser

Creating a custom XML parser involves understanding parsing mechanisms and implementing them according to requirements.

**Simple JavaScript XML Parser Example:**
```javascript
function parseXML(xmlString) {
    // Use the browser's built-in parser
    const parser = new DOMParser();
    const xmlDoc = parser.parseFromString(xmlString, "text/xml");
    
    // Check for parsing errors
    const parserError = xmlDoc.getElementsByTagName("parsererror");
    if (parserError.length > 0) {
        throw new Error("XML Parsing Error: " + parserError[0].textContent);
    }
    
    // Return the parsed document
    return xmlDoc;
}

// Function to extract data from the parsed document
function extractBookData(xmlDoc) {
    const books = [];
    const bookElements = xmlDoc.getElementsByTagName("book");
    
    for (let i = 0; i < bookElements.length; i++) {
        const book = bookElements[i];
        const title = book.getElementsByTagName("title")[0].textContent;
        const author = book.getElementsByTagName("author")[0].textContent;
        const price = parseFloat(book.getElementsByTagName("price")[0].textContent);
        const category = book.getAttribute("category");
        
        books.push({
            title: title,
            author: author,
            price: price,
            category: category
        });
    }
    
    return books;
}

// Usage example
try {
    const xmlString = `
        <?xml version="1.0" encoding="UTF-8"?>
        <bookstore>
            <book category="fiction">
                <title>Harry Potter</title>
                <author>J.K. Rowling</author>
                <price>29.99</price>
            </book>
            <book category="non-fiction">
                <title>Steve Jobs</title>
                <author>Walter Isaacson</author>
                <price>19.99</price>
            </book>
        </bookstore>
    `;
    
    const xmlDoc = parseXML(xmlString);
    const books = extractBookData(xmlDoc);
    
    console.log("Parsed Books:", books);
} catch (error) {
    console.error(error.message);
}
```

## 🎯 Mini Task 10: Comprehensive XML Project

**Final Project:** Build a Complete "Student Course Management System" using XML Technologies

This comprehensive project integrates all XML concepts you've learned. Create a complete system for managing students, courses, and enrollments.

### Project Requirements:

**1. XML Data Files (Create at least 3):**
   - `students.xml` - Student information (ID, name, email, major, enrollment year)
   - `courses.xml` - Course catalog (code, title, credits, department, instructor)
   - `enrollments.xml` - Student course enrollments (studentID, courseCode, semester, grade)

**2. XML Schema (XSD):**
   - Create `students.xsd`, `courses.xsd`, and `enrollments.xsd`
   - Use appropriate data types and constraints
   - Implement patterns for: student IDs, email addresses, course codes
   - Define value ranges for: credits (1-4), GPA (0.00-4.00), grades (A, B, C, D, F)
   - Use occurrence indicators appropriately

**3. DTD:**
   - Create an alternative DTD for at least one of your XML files
   - Include entity definitions for common values (department names, etc.)
   - Demonstrate both internal and external DTD approaches

**4. Namespaces:**
   - Create a combined document using namespaces
   - Integrate student and course data in one file using different namespaces
   - Add a third namespace for contact information

**5. XSLT Transformations (Create at least 3):**
   a) **Student Report:** Transform students.xml to HTML
      - Display as formatted table with styling
      - Sort by last name
      - Color-code by major

   b) **Course Catalog:** Transform courses.xml to HTML
      - Group courses by department
      - Show course details in cards or table
      - Include search/filter capabilities

   c) **Transcript:** Combine data from students.xml and enrollments.xml
      - Generate student transcripts
      - Calculate GPA
      - Show courses taken per semester

**6. XPath Queries (Write at least 10):**
   - Find all Computer Science majors
   - Get courses with 3+ credits
   - Find students with GPA > 3.5
   - Get all courses taught by specific instructor
   - Find students enrolled in specific course
   - Calculate average GPA
   - Count students per major
   - Find courses with no enrollments
   - Get top 5 students by GPA
   - Find students graduating this year

**7. XQuery Expressions (Write at least 5):**
   - Generate enrollment statistics report
   - List courses sorted by enrollment count
   - Create grade distribution report
   - Find students at risk (GPA < 2.0)
   - Generate department-wise student count

**8. Parsers:**
   **SAX Parser:**
   - Count total number of students
   - Extract and display all student names
   - Calculate total credits offered

   **DOM Parser:**
   - Add new student to students.xml
   - Enroll student in a course
   - Update student grade
   - Remove a course
   - Save changes back to XML file

**9. Web Interface (Optional Bonus):**
   - Create HTML pages that use JavaScript to:
     - Parse and display XML data
     - Search students/courses
     - Show enrollment statistics
     - Validate data against XSD

### Deliverables:

1. **XML Files:** All data files with proper structure
2. **Schema Files:** XSD and DTD files
3. **XSLT Files:** All transformation stylesheets
4. **Query Files:** XPath and XQuery expressions with results
5. **Parser Code:** SAX and DOM parser implementations
6. **Documentation:**
   - Project overview
   - Data dictionary (element descriptions)
   - User guide for transformations
   - Test cases and results
7. **HTML Output:** Generated reports from XSLT

### Evaluation Criteria:

- **XML Well-formedness** (10%): All XML files are well-formed
- **Schema Validation** (15%): XSD/DTD correctly validate XML
- **XSLT Quality** (20%): Transformations produce correct, styled output
- **Query Accuracy** (15%): XPath/XQuery return correct results
- **Parser Implementation** (20%): Both parsers work correctly
- **Code Quality** (10%): Clean, commented, organized code
- **Documentation** (10%): Clear, comprehensive documentation

### Bonus Challenges:

- Implement CRUD operations (Create, Read, Update, Delete) via web interface
- Add data validation using JavaScript
- Create multiple XSLT outputs (HTML, PDF, text)
- Implement search with autocomplete
- Add data visualization (charts for statistics)
- Create RESTful API to serve XML data
- Implement XML data binding

**Expected Outcome:** A fully functional course management system demonstrating mastery of all XML technologies covered in this unit.

---

**End of XML Notes - Best of luck with your XML projects!**
