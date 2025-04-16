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

## Exercises for Students

1. **Create a valid XML document** representing a music collection with albums, artists, songs, and appropriate attributes.

2. **Write an XSD schema** for the music collection XML you created.

3. **Create a DTD** for a simple blog post system with posts, comments, and authors.

4. **Write an XSLT transformation** to convert the music collection XML into an HTML table.

5. **Use XPath** to extract specific information from the music collection XML (e.g., all songs by a particular artist).

6. **Implement a simple SAX parser** to count the number of elements in an XML document.

7. **Create a DOM parser** that can modify an existing XML document (e.g., add a new song to an album).

8. **Write an XQuery** to find all albums released after a certain year and sort them by artist name.

9. **Create a namespace example** showing how to combine elements from different XML vocabularies.

10. **Develop a complete XML-based application** that demonstrates the use of XML, XSD, XSLT, and DOM/SAX parsing for a specific domain (e.g., library management, student records).
