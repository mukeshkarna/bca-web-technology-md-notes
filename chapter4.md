# Unit 4: The Server Tier - PHP

### Web Server Fundamentals

**Web Server Definition and Function**
- A web server is a computer system that receives HTTP requests via TCP and distributes information on the World Wide Web
- Main function: store, process, and deliver web pages to clients using HTTP
- Communication uses Hypertext Transfer Protocol (HTTP)
- Delivered pages are typically HTML documents, which may include images, stylesheets, and scripts
- Can also be embedded in devices like printers, routers, webcams serving only local networks

**Load Limits and Capacity**
- Web servers have *defined load limits* - they can handle only a limited number of concurrent client connections
- Server capacity depends on:
  - Own settings
  - Hardware and software limitations of OS
  - HTTP request type
  - Content origin (static or dynamic)
- When near or over limits, server becomes unresponsive

**Overload Causes:**
1. **Excessive web traffic**: Millions of clients connecting in short interval
2. **DDoS attacks**: Distributed Denial of Service attacks
3. **Computer worms**: Millions of infected computers cause abnormal traffic
4. **Server unavailability**: Required/urgent maintenance, hardware/software failures, database failures cause remaining servers to become overloaded
5. **Connection slowdowns**: Client requests served more slowly, connection count increases until server limits reached

**Anti-Overload Techniques:**
- Managing network traffic:
  - Firewalls to block unwanted traffic from bad IP sources
  - HTTP traffic managers to drop, redirect, or rewrite requests with bad HTTP patterns
  - Bandwidth management and traffic shaping
- Deploying web cache techniques
- Adding more hardware resources (RAM, disks)
- Using different domain names to serve different content via separate web servers

---

### PHP Basics

**What is PHP?**
- PHP = Hypertext Preprocessor
- Server-side scripting language embedded in HTML
- Used to manage dynamic content, databases, session tracking, and build e-commerce sites

**Simple PHP Example:**
```php
<html>
<head>
    <title>Hello World</title>
</head>
<body>
    <?php
    echo "Today is " . date("l") . ".";
    ?>
</body>
</html>
```
*Output: "Today is Thursday." (displays current day)*

Date format characters:
- `d` - Day of month (01 to 31)
- `m` - Month (01 to 12)
- `Y` - Year (four digits)
- `l` (lowercase 'L') - Day of week

---

**Variables in PHP**

All variables begin with `$` sign and are followed by a concise, meaningful name. PHP has 8 data types:
1. Integers
2. Doubles
3. Booleans
4. NULL
5. Strings
6. Arrays
7. Objects
8. Resources

**Variable Declaration Examples:**
```php
$int_var = 12345;
$name = "ronaldo";
$my_var = NULL;
```

**Variable Naming Rules:**
- Must begin with letter or underscore character
- Can consist of numbers, letters, underscores
- **Cannot** use characters like `+`, `-`, `%`, `(`, `)`, `.`, `&`, etc.

---

**Comments in PHP**

Two types of comments:

**Single-line comments:**
```php
<?
# This is a single line comment
// This is also a single line comment
?>
```

**Multi-line comments:**
```php
<?
/* This is a
   multi-line
   comment
   for detailed explanations
*/
echo "comments are not displayed"
?>
```

---

### Control Flow Structures

**For Loop**

Used when you know exactly how many times to execute a statement.

**Syntax:**
```php
for(start value, condition, increment/decrement) {
    //statements
}
```

**Example:**
```php
<?php
for($i = 1; $i <= 10; $i++) {
    echo "Number: " . $i . "<br>";
}
?>
```
*Output: Displays numbers 1 through 10, each on new line*

---

**While Loop**

Executes a block of code if and as long as test expression is true.

**Syntax:**
```php
while (condition) {
    // code to be executed;
}
```

**Example:**
```php
<?php
$count = 1;
while ($count <= 5) {
    echo "Count is: " . $count . "<br>";
    $count++;
}
?>
```
*Output:*
```
Count is: 1
Count is: 2
Count is: 3
Count is: 4
Count is: 5
```

---

**Do-While Loop**

Executes code block at least once, then repeats the loop as long as condition is true.

**Syntax:**
```php
do {
    //code to be executed;
}
while (condition);
```

**Example:**
```php
<?php
$num = 1;
do {
    echo "The number is: " . $num . "<br>";
    $num++;
} while ($num <= 3);
?>
```
*Output:*
```
The number is: 1
The number is: 2
The number is: 3
```

---

**Foreach Loop**

Used to loop through arrays. For each pass, the value of current array element is assigned to `$value` and array pointer moves by one.

**Syntax:**
```php
foreach (array as value) {
    code to be executed;
}
```

**Example:**
```php
<?php
$colors = array("red", "green", "blue", "yellow");
foreach ($colors as $value) {
    echo $value . "<br>";
}
?>
```
*Output:*
```
red
green
blue
yellow
```

---

**Switch Statement**

Evaluates given expression, searches for matching value. If match found, associated code executes; otherwise default code executes.

**Syntax:**
```php
switch (expression) {
    case 1:
        //code to be executed if expression matches case 1;
        break;
    case 2:
        // code to be executed if expression matches case 2;
        break;
    .....
    ....
    default:
        //code to be executed if none of the cases match
}
```

**Example:**
```php
<?php
$day = "Monday";
switch ($day) {
    case "Monday":
        echo "Today is Monday";
        break;
    case "Tuesday":
        echo "Today is Tuesday";
        break;
    case "Wednesday":
        echo "Today is Wednesday";
        break;
    default:
        echo "Today is another day";
}
?>
```
*Output: "Today is Monday"*

---

**If-Else Statement**

Execute some code if condition is true, another code if condition is false.

**Syntax:**
```php
if (condition) {
    //code to be executed if condition is true;
}
else {
    //code to be executed if condition is false;
}
```

**Example:**
```php
<?php
$age = 18;
if ($age >= 18) {
    echo "You are eligible to vote";
}
else {
    echo "You are not eligible to vote";
}
?>
```
*Output: "You are eligible to vote"*

---

### Session and State Management

**Understanding Sessions**

Web is **stateless** - the web server doesn't know who you are and what you do because HTTP doesn't maintain state. If user inserts information and moves to next page, that data will be lost.

**Solution**: Store information about user using **Sessions**
- Sessions provide facility to store information on server memory
- Session variables hold information about one single user
- Available to all pages in one application
- By default, session variables last until user closes browser

---

**Creating a Session**

Simply call `session_start()` function. Session variables are set with the `$_SESSION` global variable.

**Syntax:**
```php
session_start();
```

This must be at the top of script on each page where session is needed.

**Setting Session Variables:**

**Syntax:**
```php
$_SESSION['session_name'] = "value";
```

**Example:**
```php
<?php
// Start the session
session_start();
?>
<!DOCTYPE html>
<html>
<body>
<?php
// Set session variables
$_SESSION["name"] = "rabin";
$_SESSION["address"] = "kathmandu";
?>
</body>
</html>
```

---

**Retrieving Session Values**

Can retrieve values on any page if session value was stored.

**Syntax:**
```php
$_SESSION['session_name']
```

**Example:**
```php
<?php
session_start();
?>
<!DOCTYPE html>
<html>
<body>
<?php
// Echo session variables that were set on previous page
echo "hello " . $_SESSION["name"] . ".<br>";
echo "your address is " . $_SESSION["address"] . ";
?>
</body>
</html>
```
*Output:*
```
hello rabin.
your address is kathmandu
```

---

**Removing Session Variables**

Can destroy session after finished using it.

**To destroy specific session variable:** Use `unset()` function
**To destroy all session variables:** Use `session_destroy()` function

**Syntax:**
```php
session_destroy(); //destroy all the session
unset($_SESSION['session_name']); //unset single variable
```

**Example:**
```php
<?php
session_start();
?>
<!DOCTYPE html>
<html>
<body>
<?php
// remove name variables
unset($_SESSION['name']);
// destroy the session
session_destroy();
?>
</body>
</html>
```

---

**Advantages of Sessions:**
- Helps maintain user states and data across the application
- Can easily be implemented and store any kind of object
- Stores every client data separately
- Session is secure and transparent from user

**Disadvantages of Sessions:**
- Performance overhead with large volume of users (session data stored in server memory)
- Overhead in serializing and de-serializing session data (especially for StateServer and SQLServer modes)

---

### Error Handling

**Default Error Handling**

PHP's default error handling is simple: error message with filename, line number, and description sent to browser.

**Example of default error:**
```
Warning: fopen(welcome.txt) [function.fopen]: failed to open stream:
No such file or directory in C:\webfolder\hello.php on line 2
```

---

**Using die() Function**

Handle errors by checking if required operation can be performed, then use `die()` statement.

**Example:**
```php
<?php
if(!file_exists("welcome.txt")) {
    die("File not found");
} else {
    $file = fopen("welcome.txt", "r");
}
?>
```
*If file doesn't exist, output: "File not found"*

This is better than default error message, but stopping script isn't always the right approach.

---

**Custom Error Handlers**

Create a special function that can be called when error occurs. This function must handle minimum two parameters (error level and error message) but can accept up to five parameters (optionally: file, line-number, error context).

**Syntax:**
```php
error_function(error_level, error_message,
               error_file, error_line, error_context)
```

**Parameters:**
- **error_level**: Required. Specifies error report level for user-defined error (must be value number)
- **error_message**: Required. Specifies error message for user-defined error
- **error_file**: Optional. Specifies filename where error occurred
- **error_line**: Optional. Specifies line number where error occurred
- **error_context**: Optional. Specifies array containing every variable and their values in use when error occurred

---

**Custom Error Handler Example:**

```php
<html>
<head>
    <title>custom error</title>
    <style type="text/css">
        .notice{color:yellow;}
        .warning{color:red;}
    </style>
</head>
<body>
<?php
set_error_handler("myhandler");
error_reporting(E_ALL);

//generate some error
echo $var;
echo 1/0;

//custom error handler
function myhandler($type, $msg, $file, $line, $context) {
    $type = "an error occur on line.$line while processing your request."
    switch($type) {
        case E_NOTICE:
            echo "<div class=\"notice\">$text</div>";
            break;
        case E_WARNING:
            echo "<div class=\"warning\">$text<div>";
            break;
    }
}
?>
</body>
</html>
```

This example:
1. Sets custom error handler with `set_error_handler("myhandler")`
2. Enables all error reporting with `error_reporting(E_ALL)`
3. Generates errors: undefined variable `$var` and division by zero
4. Custom handler displays errors with different styling based on error type

---

**Error Reporting**

Control which errors are displayed using built-in `error_reporting()` function.

**To display only fatal errors:**
```php
<?php
//only display fatal errors
error_reporting(E_ERROR);
echo 1/0;
?>
```

**To turn off runtime fatal errors:**
```php
<?php
//only display warnings
error_reporting(E_WARNING);
echo somefunc();
?>
```

**To display notice and fatal errors:**
```php
<?php
//only display notice and fatal errors
error_reporting(E_NOTICE | E_ERROR);
echo $var; //notice
echo 1/0; //warning
echo myfun(); //fatal
?>
```

**Note**: `error_reporting()` doesn't automatically make script error-free. It only hides errors of certain types. Can also pass combination of error levels to customize errors.

---

**Error Types:**

1. **Notice**: Small, non-critical errors that don't stop PHP from executing script (e.g., accessing undefined variable)

2. **Warnings**: Serious errors requiring attention but don't stop script execution (e.g., reading file that doesn't exist, division by zero)

3. **Fatal Errors**: Critical syntax or runtime errors that stop execution (e.g., calling non-existent function, instantiating object of non-existent class)

---

**Error Report Levels:**

- `E_WARNING`
- `E_NOTICE`
- `E_USER_ERROR`
- `E_USER_WARNING`
- `E_USER_NOTICE`
- `E_RECOVERABLE_ERROR`
- `E_ALL` (all errors and warnings)

---

### Exception Handling

**What is Exception Handling?**

Used to change normal flow of code execution if a specified error (exceptional) condition occurs. This condition is called an **exception**.

**Normal Exception Flow:**
1. Current code state is saved
2. Code execution switches to predefined (custom) exception handler function
3. Depending on situation, handler may:
   - Resume execution from saved code state
   - Terminate script execution
   - Continue script from different location in code

---

**Basic Use of Exception**

When exception is thrown, code following it will not be executed, and PHP will try to find matching "catch" block.

**Simple Example:**
```php
<?php
//create function with an exception
function checknum($number) {
    if ($number > 1) {
        throw new Exception("Value must be 1 or below");
    }
    return true;
}

//trigger exception
checkNum(2);
?>
```

**Output:**
```
Fatal error: Uncaught exception 'Exception'
with message 'Value must be 1 or below' in C:\webfolder\test.php:6
Stack trace: #0 C:\webfolder\test.php(12):
checkNum(28) #1 {main} thrown in C:\webfolder\test.php on line 6
```

The error generates because try and catch is not defined to handle the error.

---

**Try-Throw-Catch Structure**

Proper exception code should include:

1. **Try**: Function using exception should be in "try" block. If exception doesn't trigger, code continues normally. If exception triggers, exception is "thrown"

2. **Throw**: How you trigger an exception. Each "throw" must have at least one "catch"

3. **Catch**: "catch" block retrieves exception and creates object containing exception information

**Syntax:**
```php
try {
    // code that may throw exception
}
catch (Exception $e) {
    // code to handle exception
}
```

---

**Complete Exception Example:**

```php
<?php
//create function with an exception
function checkNum($number) {
    if($number > 1) {
        throw new Exception("Value must be 1 or below");
    }
    return true;
}

//trigger exception in a "try" block
try {
    checkNum(2);
    //If the exception is thrown, this text will not be shown
    echo 'If you see this, the number is 1 or below';
}

//catch exception
catch(Exception $e) {
    echo 'Message: ' . $e->getMessage();
}
?>
```

**Output:**
```
Message: Value must be 1 or below
```

**Explanation:**
1. `checkNum()` function created - checks if number greater than 1, throws exception if true
2. `checkNum()` called in "try" block
3. Exception within `checkNum()` is thrown
4. "catch" block retrieves exception and creates object ($e) containing exception information
5. Error message echoed by calling `$e->getMessage()` from exception object

---

**Creating Custom Exception Class**

Creating custom error handler is simple. Create special class with functions that can be called when exception occurs in PHP.

The class must be extension of Exception class. Custom exception class inherits properties from PHP's Exception class and can add custom functions to it.

**Custom Exception Example:**

```php
<?php
class customException extends Exception {
    public function errorMessage() {
        //error message
        $errorMsg = 'Error on line ' . $this->getLine() . ' in ' . $this->getFile()
                  . ': <b>' . $this->getMessage() . '</b> is not a valid E-Mail address';
        return $errorMsg;
    }
}

$email = "someone@example...com";
try {
    //check if
    if(filter_var($email, FILTER_VALIDATE_EMAIL) === FALSE) {
        //throw exception if email is not valid
        throw new customException($email);
    }
}
catch (customException $e) {
    //display custom message
    echo $e->errorMessage();
}
?>
```

**Explanation:**
1. `customException()` class created as extension of old exception class - inherits all methods and properties from old class
2. `errorMessage()` function created - returns error message if e-mail address is invalid
3. `$email` variable set to string that is not a valid e-mail address
4. "try" block executed and exception thrown since e-mail address is invalid
5. "catch" block catches exception and displays error message

---

### Tag Libraries

**What are Tag Libraries?**

In web applications, common design goal is to separate display code from business logic. Java tag libraries are solution to this problem.

- Allow you to isolate business logic from display code
- Create Tag class (performs business logic)
- Include HTML-like tag in JSP page
- When Web server encounters tag, it calls methods within corresponding Java Tag class to produce required HTML content

**Purpose**: Separate presentation layer from business logic layer

---

**The taglib Directive**

Java Server page API allows us to define custom JSP tags that look like HTML or XML tags. Tag library is set of user-defined tags that implement custom behaviour.

**Syntax:**
```jsp
<%@taglib prefix="prefixOfTag" uri="uri"%>
```

Where:
- **uri** attribute value resolves to location the container understands
- **prefix** attribute informs container what bits of markup are custom actions

---

**Creating Custom Tag**

Custom tag is user-defined JSP language element. When JSP page containing custom tag is translated into servlet, tag is converted to operations on object called **tag handler**. 

Web container then invokes those operations when JSP page's servlet is executed.

JSP tag extensions let you create new tags that can insert directly into JavaServer Page just as you would built-in tags.

JSP 2.0 specification introduced Simple Tag Handlers for writing these custom tags.

---

**Simple Custom Tag Example:**

To write custom tag, extend `SimpleTagSupport` class and override `doTag()` method where you place code to generate content for tag.

**Create Tag Handler (HelloTag.java):**

```java
package com.customTagExample;
import javax.servlet.jsp.tagext.*;
import javax.servlet.jsp.*;
import java.io.*;

public class HelloTag extends SimpleTagSupport {
    public void doTag() throws JspException, IOException {
        JspWriter out = getJspContext().getOut();
        out.println("Hello Custom Tag!");
    }
}
```

**Explanation:**
- `doTag()` method takes current `JspContext` object using `getJspContext()` method
- Uses it to send "Hello Custom Tag!" to current `JspWriter` object

---

**Create Tag Library Descriptor (TLD) File:**

```xml
<taglib>
    <tlib-version>1.0</tlib-version>
    <jsp-version>2.0</jsp-version>
    <short-name>Example TLD</short-name>
    <tag>
        <name>Hello</name>
        <tag-class>com.customTagExample.HelloTag</tag-class>
        <body-content>empty</body-content>
    </tag>
</taglib>
```

Save this as `custom.tld` in `<Tomcat-Installation-Directory>\webapps\ROOT\WEB-INF\` directory.

---

**Use Custom Tag in JSP:**

```jsp
<%@ taglib prefix="ex" uri="WEB-INF/custom.tld"%>
<html>
<head>
    <title>A sample custom tag</title>
</head>
<body>
    <ex:Hello/>
</body>
</html>
```

**Output:**
```
Hello Custom Tag!
```

---

**Accessing the Tag Body:**

You can include message in body of tag as seen with standard tags.

**Custom Tag with Body:**

```jsp
<ex:Hello>
    This is message body
</ex:Hello>
```

When tag has body content, modify `doTag()` method to process and return enclosed body content.

---

# Unit 5: Introduction to Advanced Server Side Issues

### Form Validation

**Why Validate Form Data?**

Validation is necessary to prevent attackers from exploiting code by injecting HTML or JavaScript code.

**Security Issue Example:**

User form with fields:
```html
<form>
    Name: <input type="text" name="name">
    Email: <input type="text" name="email">
</form>
```

If user enters: `<script>alert('Hacked!')</script>` in name field, without validation, this script will execute on the page.

---

**Using htmlspecialchars() Function**

The way we should do validation is pass all variables through PHP's `htmlspecialchars()` function.

This function replaces HTML class like `<` and `>` to their HTML version `&lt;` and `&gt;`, etc.

**Example:**

```php
<?php
$name = htmlspecialchars($_POST['name']);
$email = htmlspecialchars($_POST['email']);
?>
```

Now much safer - prevents attackers from exploiting code by injecting HTML or JavaScript code.

---

**Creating Validation Function**

If we know exactly what kind of data to expect, we can make further steps to ensure user has entered what we want.

Two more things to do:
1. Strip unnecessary characters from data
2. If quotes are escaped with slash (\), remove that

Instead of writing same code repeatedly, create function that does all checking.

**check_input() Function:**

```php
<?php
$name = check_input($_POST['name']);
$email = check_input($_POST['email']);
?>
</html>
<?php
function check_input($data) {
    $data = trim($data);
    $data = stripslashes($data);
    $data = htmlspecialchars($data);
    return $data;
}
?>
```

**Function does:**
1. `trim($data)` - Strips unnecessary characters
2. `stripslashes($data)` - Removes backslashes
3. `htmlspecialchars($data)` - Converts special characters to HTML entities
4. Returns sanitized data

---

### Required and Optional Fields

Many times we want to make input fields required.

**Modified check_input() Function with Required Field:**

```php
<?php
function check_input($data, $problem = "error") {
    $data = trim($data);
    $data = stripslashes($data);
    $data = htmlspecialchars($data);
    
    if($problem && strlen($data) == 0) {
        die($problem)
    }
    return $data;
}
?>
```

Now if field is empty and `$problem` is set, script will stop and display error message.

---

**Complete Form Validation Example:**

```php
<?php
$name = check_input($_POST['name'], "Please enter your name");
$email = check_input($_POST['email'], "Please enter your email");
$message = check_input($_POST['message']); // Optional field

function check_input($data, $problem = "") {
    $data = trim($data);
    $data = stripslashes($data);
    $data = htmlspecialchars($data);
    
    if($problem && strlen($data) == 0) {
        die($problem);
    }
    return $data;
}
?>
```

In this example:
- `name` and `email` are required (will die with error message if empty)
- `message` is optional (no error message parameter)

---

### Validate Email Address

There's no way to be 100% sure email is actually working unless we send email. But we can check if email syntax is valid.

**Simple Email Validation:**

```php
$email = htmlspecialchars($_POST['email']);
if(!preg_match("/([\w\-] + \@[\w\-] +)/", $email)) {
    die("Email address not valid");
}
```

**Explanation:**
- Uses `preg_match()` function with regular expression
- Pattern checks for: `word characters + @ + word characters`
- Dies with error if email doesn't match pattern

**Regular Expression Breakdown:**
- `[\w\-]+` - One or more word characters or hyphens
- `\@` - Literal @ symbol
- `[\w\-]+` - One or more word characters or hyphens

---

### Validate URL Address

If we have input field named "website", can check for valid URL.

**URL Validation:**

```php
$url = htmlspecialchars($_POST['website']);
if(!preg_match("/^(http?:W + ]\w\-] + \ [\w\-] +)/", $(m))) {
    die("URL address not valid");
}
```

**Pattern checks for:**
- `http?:` - http or https protocol
- `W+` - Domain characters
- `[\w\-]+` - Domain name with word characters or hyphens
- `\` - Dot separator
- `[\w\-]+` - Top-level domain

---

### Additional Validation Patterns

**Digit 0-9 Only:**
```php
if(preg_match("/^\D/", $age)) {
    die("Please enter numbers only for age.");
}
```
- `/^\D/` - Matches if string starts with non-digit character

---

**Letters a-z and A-Z Only:**
```php
if(preg_match("/[^,a-z A-Z]/", $text)) {
    die("Please enter letters only!");
}
```
- `/[^,a-z A-Z]/` - Matches any character that's not a letter

---

**Anything but Whitespace:**
```php
if(Preg_match("/^\S/", $text)) {
    die("don't enter any space");
}
```
- `/^\S/` - Matches non-whitespace at start

---

### Database Connectivity in PHP

**Introduction**

In PHP, we use database to store details.

When we create new database, must specify first arguments to mysqli object: **servername, username, and password**.

---

**Create Connection**

```php
<?php
$servername = "localhost";
$username = "username";
$password = "password";

// create connection
$con = mysqli_connect($servername, $username, "");

// check connection
if($con) {
    die("connection failed:" . mysqli_error());
}
?>
```

**Explanation:**
1. Set server details (localhost for local development)
2. Create connection using `mysqli_connect()`
3. Check if connection successful
4. Display error if connection fails using `mysqli_error()`

---

**Create Database**

```php
$sql = "CREATE DATABASE myDB";
if(mysqli_query($con, $sql)) {
    Echo "Database Created";
}
else {
    Echo "Error:" . mysqli_error($con);
}
```

**Steps:**
1. Create SQL query string
2. Execute query using `mysqli_query()`
3. Check if successful
4. Display appropriate message

---

**Create Table**

The CREATE TABLE statement is used to create table in MySQL.

**Example - Create "MyGuests" table:**

```php
CREATE TABLE MyGuests(
    id INT(6) UNSIGNED AUTO_INCREMENT PRIMARY KEY,
    firstname VARCHAR(20) NOT NULL,
    lasrtname VARCHAR(20) NOT NULL,
    email VARCHAR(50),
    reg_date TIMESTAMP
)
```

**In PHP:**

```php
// create connection first. Then,

// sql to create table
$sql = "CREATE TABLE MyGuests(
    id INT(6) UNSIGNED AUTO_INCREMENT PRIMARY KEY,
    firstname VARCHAR(20) NOT NULL,
    lastname VARCHAR(20) NOT NULL,
    email VARCHAR(50),
    reg_date TIMESTAMP)";
    
if(mysqli_query($con, $sql)) {
    echo "Table Created";
}
else {
    echo "Error";
}
```

**Table Structure:**
- `id`: Auto-incrementing primary key (6 digits, unsigned)
- `firstname`: Variable character field, 20 characters max, cannot be null
- `lastname`: Variable character field, 20 characters max, cannot be null
- `email`: Variable character field, 50 characters max
- `reg_date`: Timestamp, automatically records when record created

---

### Insert Data into Database

After database and table created, can start adding data.

**Rules:**
- SQL query must be quoted in PHP
- String values inside SQL query must be quoted
- Numeric values must NOT be quoted

---

**Insert Data Example:**

```php
//after database connection

$sql = "INSERT INTO MyGuests(firstname, lastname, email) VALUES('John', 'Doe', 'john@ex.com')";

if(mysqli_query($con, $sql)) {
    echo "New record Created";
}
else {
    echo "Error:" . mysqli_error($con);
}

mysqli_close($con);
```

**Explanation:**
1. Create INSERT SQL statement
2. Specify table name and columns
3. Provide VALUES for each column
4. Execute query
5. Check for success/failure
6. Close connection when done

---

**Insert Multiple Records:**

```php
$sql = "INSERT INTO MyGuests(firstname, lastname, email) VALUES('John', 'Doe', 'john@ex.com')";
$sql = "INSERT INTO MyGuests(firstname, lastname, email) VALUES('Mary', 'Moe', 'mary@ex.com')";

if(mysqli_multi_query($con, $sql)) {
    Echo "New records added";
}
else {
    echo "Error";
}

mysqli_close($con);
```

**Note:** Use `mysqli_multi_query()` instead of `mysqli_query()` for multiple queries.

---

### Select Data from Database

The SELECT statement is used to select data from one or more tables.

**Syntax:**
```sql
SELECT column_name(s) FROM table_name
```

Or use `*` character to select ALL columns:
```sql
SELECT * FROM table_name
```

---

**Select Data Example:**

```php
<?php
//create connection
$con = mysqli_connect('localhost', "user", "");

if($con) {
    die("connection failed");
}

$sql = "SELECT id, firstname FROM MyGuests;

$result = mysqli_query($con, $sql);

if(mysqli_num_rows($result) > 0) {
    while($row = mysqli_fetch_assoc($result)) {
        echo "id:" . $row["id"] . "_name:" . $row["firstname"] . "." . "<br>";
    }
}
else {
    echo "0 results";
}

mysqli_close($con);
?>
```

**Explanation:**
1. Create database connection
2. Write SELECT query to get id and firstname
3. Execute query and store result
4. Check if any rows returned using `mysqli_num_rows()`
5. If rows exist, loop through them with `mysqli_fetch_assoc()`
6. Each row returned as associative array
7. Access columns using array keys: `$row["id"]`, `$row["firstname"]`
8. Close connection when done

**Output format:**
```
id:1_name:John.
id:2_name:Mary.
```

---

### Delete Data from Database

The DELETE statement is used to delete records from table.

**Syntax:**
```sql
DELETE FROM table_name WHERE some_column = some_value
```

**Important:** WHERE clause specifies which record(s) should be deleted. If you omit WHERE clause, ALL records will be deleted!

---

**Delete Data Example:**

```php
//sql to delete a record
$sql = "DELETE FROM MyGuests WHERE id = 3;

if(mysqli_query($con, $sql)) {
    echo "Record deleted successfully";
}
else {
    echo "Error";
}

mysqli_close($con);
?>
```

**Explanation:**
1. Create DELETE SQL statement
2. Use WHERE clause to specify which record (id = 3)
3. Execute query
4. Check for success
5. Close connection

**Warning:** Without WHERE clause, query would delete ALL records:
```sql
DELETE FROM MyGuests; -- Deletes everything!
```

---

### Update Data in Database

The UPDATE statement is used to update existing records in table.

**Syntax:**
```sql
UPDATE table_name
SET column1 = value1, column2 = value2
WHERE some_column = some_value
```

**Note:** WHERE clause specifies which record(s) should be updated. If omit WHERE clause, ALL records will be updated.

---

**Update Data Example:**

```php
<?php
//create connection
$con = mysqli_connect("localhost", "user", "");

//check connection
if($con) {
    die("connection failed");
}

$sql = UPDATE MyGuests SET lastname = 'Doe' WHERE id = "2";

if(mysqli_query($con, $sql)) {
    echo "Record updated successfully";
}
?>
```

**Explanation:**
1. Establish database connection
2. Create UPDATE SQL statement
3. SET clause specifies what to change (lastname = 'Doe')
4. WHERE clause specifies which record (id = "2")
5. Execute query
6. Display success message

**Result:** Record with id=2 will have lastname changed to 'Doe'

---

### Authentication in Database

We can authenticate user in database using GRANT query.

**Grant Privileges Syntax:**
```sql
Grant all privileges on *.* → all tables
to username@localhost identified by "password" with grant option
```

**Example:**
```sql
grant create, insert, update, select
on Mydb.*
to ram@localhost
identified by "abc";
with grant option;
```

**Explanation:**
- Grants CREATE, INSERT, UPDATE, SELECT privileges
- On all tables in Mydb database (Mydb.*)
- To user 'ram' connecting from localhost
- With password "abc"
- WITH GRANT OPTION allows user to grant privileges to others

---

**Remove Authentication - REVOKE Query**

To remove authentication from user, use REVOKE query.

**Syntax:**
```sql
revoke all privileges
on *.*
from username@localhost;
```

**Example:**
```sql
revoke create, delete
on Mydb.*
from ram@localhost
```

**Explanation:**
- Revokes CREATE and DELETE privileges
- From all tables in Mydb database
- From user 'ram@localhost'

**Note:** RESTRIC - If authorization is given to only one user, otherwise CASCADE

---

### Authentication by IP Address

In some rare instances, we may wish to limit access to certain page or pages to certain IP addresses.

**Use Cases:**
- Internal network with publicly viewable website - certain pages viewable only by certain machines on internal network
- Remote website - restrict access to certain page/pages so only we (from static IP address) can access those pages

**How it works:**
- Determine IP addresses of user trying to view pages
- Check against set value
- If IP address matches, page can be viewed

**Security Note:**
- Could be fooled by IP spoofing or other hacks
- Should NOT be used to protect sensitive information (credit card numbers, proprietary information)
- Simple method that protects pages from majority of users surfing net

**Important:** 
- Your computer may have more than one IP address
- Browser may report different IP than you're attempting to verify
- This is especially true when browser and web server reside on same machine (when testing)

---

**Authentication by IP - Example:**

```php
<?php
$accept = array("127", "0", "0", "1");
$remote = explode("." $REMOTE_ADDR);
$match = 1;

for($i=0; $i<sizeof($accept); $i++) {
    if($remote[$i] != $accept[$i]) {
        $match = 0;
    }
}

if($match) {
    echo "<h2>Access Granted</h2>";
}
else {
    echo "<h2>Access Forbidden</h2>";
}
?>
```

**Explanation:**
1. `$accept` array contains allowed IP address (127.0.0.1 = localhost)
2. `$remote` gets user's IP from `$REMOTE_ADDR` and splits by dot using `explode()`
3. `$match` flag initialized to 1 (true)
4. Loop compares each part of IP address
5. If any part doesn't match, set `$match = 0`
6. Finally check if `$match` still true
7. Grant/deny access accordingly

**Example:**
- If user accessing from IP 127.0.0.1: Access Granted
- If user accessing from IP 192.168.0.1: Access Forbidden

**Advanced version** could check multiple allowed IPs or IP ranges.

---

### Cookies

**What are Cookies?**

Cookies are small files that server embeds on user's computer. Each time same computer requests page with browser, it will send cookie too. With PHP, you can both create and retrieve cookie values.

**Cookie Characteristics:**
- Maximum size: Constraint on data per cookie is **4 KB**
- Stored on client machine
- Can be read by client-side scripts
- Have expiration dates
- Domain and path specific

---

**Setting Cookies**

Cookies are created with `setcookie()` function.

**Syntax:**
```php
setcookie(name, value, expire, path, domain, secure, httponly);
```

**Parameters:**
- **name**: Required. Cookie name
- **value**: Required. Cookie value
- **expire**: Optional. Expiration timestamp
- **path**: Optional. Server path where cookie available
- **domain**: Optional. Domain name where cookie available
- **secure**: Optional. If TRUE, cookie only transmitted over HTTPS
- **httponly**: Optional. If TRUE, cookie accessible only through HTTP protocol

**Only name parameter is required.** All other parameters are optional.

---

**Cookie Examples:**

**Simple Cookie (expires when browser closes):**
```php
<?php
$cookie_name = "user";
$cookie_value = "John Doe";
setcookie($cookie_name, $cookie_value);
?>
```

---

**Cookie with 30-day expiration:**
```php
<?php
$cookie_name = "user";
$cookie_value = "John Doe";
setcookie($cookie_name, $cookie_value, time() + (86400 * 30), "/");
// 86400 = 1 day in seconds
?>
<html>
<body>
<?php
echo "Cookie named '" . $cookie_name . "' is set!";
?>
</body>
</html>
```

**Explanation:**
- `time()` returns current Unix timestamp
- `86400 * 30` = seconds in 30 days
- `"/"` makes cookie available across entire website

---

**Retrieving Cookie Value:**

```php
<?php
if(isset($_COOKIE[$cookie_name])) {
    echo "Cookie '" . $cookie_name . "' is set!<br>";
    echo "Value is: " . $_COOKIE[$cookie_name];
}
else {
    echo "Cookie named '" . $cookie_name . "' is not set!";
}
?>
```

**Explanation:**
- Check if cookie exists using `isset()`
- Access cookie value through `$_COOKIE` superglobal array
- Cookie name used as array key

**Output (if cookie exists):**
```
Cookie 'user' is set!
Value is: John Doe
```

---

**Modifying Cookie:**

To modify cookie, just set it again with new value:

```php
<?php
$cookie_name = "user";
$cookie_value = "Jane Smith";
setcookie($cookie_name, $cookie_value, time() + (86400 * 30), "/");
?>
```

---

**Deleting Cookie:**

To delete cookie, use `setcookie()` with expiration date in the past:

```php
<?php
// set the expiration date to one hour ago
setcookie("user", "", time() - 3600);
?>
<html>
<body>
<?php
echo "Cookie 'user' is deleted.";
?>
</body>
</html>
```

**Explanation:**
- `time() - 3600` sets expiration to 1 hour ago
- Empty string for value
- This tells browser to delete the cookie

---

**Check if Cookies are Enabled:**

```php
<?php
setcookie("test_cookie", "test", time() + 3600, '/');
?>
<html>
<body>
<?php
if(count($_COOKIE) > 0) {
    echo "Cookies are enabled.";
}
else {
    echo "Cookies are disabled.";
}
?>
</body>
</html>
```

**Explanation:**
- Create test cookie
- Check if `$_COOKIE` array has any cookies
- If count > 0, cookies are enabled

---

### File Handling

PHP has various functions to create, read, upload, and edit files.

**Common File Operations:**
- Read files
- Write to files  
- Append to files
- Create new files
- Delete files
- Upload files

---

**Opening Files - fopen()**

```php
$file = fopen("welcome.txt", "r");
```

**File Modes:**
- **r**: Read only, starts at beginning of file
- **r+**: Read/Write, starts at beginning
- **w**: Write only, opens and truncates file to 0 length (creates if doesn't exist)
- **w+**: Read/Write, opens and truncates to 0 length (creates if doesn't exist)
- **a**: Write only, opens and sets pointer to end (creates if doesn't exist)
- **a+**: Read/Write, opens and sets pointer to end (creates if doesn't exist)
- **x**: Create and open for writing only (fails if file exists)
- **x+**: Create and open for reading and writing (fails if file exists)

---

**Reading Files - fread()**

```php
<?php
$file = fopen("welcome.txt", "r") or die("Unable to open file!");
echo fread($file, filesize("welcome.txt"));
fclose($file);
?>
```

**Explanation:**
1. Open file in read mode
2. Use `or die()` to handle error if file doesn't exist
3. `fread()` reads entire file
4. `filesize()` gets size of file in bytes
5. `fclose()` closes file when done

---

**Reading Single Line - fgets()**

```php
<?php
$file = fopen("welcome.txt", "r");
echo fgets($file);
fclose($file);
?>
```

Reads one line and stops. Call multiple times to read multiple lines.

---

**Reading Character by Character - fgetc()**

```php
<?php
$file = fopen("welcome.txt", "r");
while(!feof($file)) {
    echo fgetc($file);
}
fclose($file);
?>
```

**Explanation:**
- `fgetc()` reads single character
- `feof()` checks if end-of-file reached
- Loop continues until end of file

---

**Writing to Files - fwrite()**

```php
<?php
$file = fopen("test.txt", "w") or die("Unable to open file!");
$txt = "John Doe\n";
fwrite($file, $txt);
$txt = "Jane Doe\n";
fwrite($file, $txt);
fclose($file);
?>
```

**Explanation:**
- Open file in write mode (creates if doesn't exist)
- `fwrite()` writes string to file
- `\n` adds newline
- Each `fwrite()` adds to file
- Close file when done

**Warning:** Opening in 'w' mode overwrites existing content!

---

**Appending to Files:**

```php
<?php
$file = fopen("test.txt", "a");
$txt = "Mickey Mouse\n";
fwrite($file, $txt);
fclose($file);
?>
```

Using 'a' mode appends to end without overwriting.

---

**Creating New File:**

If use `fopen()` on file that doesn't exist, will create it (given file opened for writing (w) or appending (a)):

```php
<?php
$file = fopen("newfile.txt", "w");
?>
```

---

**Deleting Files - unlink()**

```php
<?php
if(file_exists("test.txt")) {
    unlink("test.txt");
    echo "File deleted";
}
else {
    echo "File does not exist";
}
?>
```

**Best practice:** Always check if file exists before trying to delete.

---

### File Upload

PHP allows uploading files to server.

**HTML Upload Form:**

```html
<form action="upload.php" method="post" enctype="multipart/form-data">
    Select file to upload:
    <input type="file" name="fileToUpload" id="fileToUpload">
    <input type="submit" value="Upload File" name="submit">
</form>
```

**Important form attributes:**
- `method="post"`: File upload requires POST
- `enctype="multipart/form-data"`: Specifies content type for submitting form

---

**PHP Upload Script (upload.php):**

```php
<?php
$target_dir = "uploads/";
$target_file = $target_dir . basename($_FILES["fileToUpload"]["name"]);
$uploadOk = 1;
$imageFileType = strtolower(pathinfo($target_file, PATHINFO_EXTENSION));

// Check if file already exists
if (file_exists($target_file)) {
    echo "Sorry, file already exists.";
    $uploadOk = 0;
}

// Check file size (limit to 5MB)
if ($_FILES["fileToUpload"]["size"] > 5000000) {
    echo "Sorry, your file is too large.";
    $uploadOk = 0;
}

// Allow certain file formats
if($imageFileType != "jpg" && $imageFileType != "png" && $imageFileType != "jpeg") {
    echo "Sorry, only JPG, JPEG, & PNG files are allowed.";
    $uploadOk = 0;
}

// Check if $uploadOk is set to 0 by an error
if ($uploadOk == 0) {
    echo "Sorry, your file was not uploaded.";
}
else {
    if (move_uploaded_file($_FILES["fileToUpload"]["tmp_name"], $target_file)) {
        echo "The file " . basename($_FILES["fileToUpload"]["name"]) . " has been uploaded.";
    }
    else {
        echo "Sorry, there was an error uploading your file.";
    }
}
?>
```

**Explanation:**
1. `$_FILES` superglobal contains uploaded file information
2. `$_FILES["fileToUpload"]["name"]` = original filename
3. `$_FILES["fileToUpload"]["tmp_name"]` = temporary location on server
4. `$_FILES["fileToUpload"]["size"]` = file size in bytes
5. `$_FILES["fileToUpload"]["type"]` = MIME type
6. Check if file exists, size limit, allowed types
7. `move_uploaded_file()` moves from temp location to permanent location

---

### XML Parsers

**What is XML Parser?**

Software that reads and parses XML, passing data to invoking application. Application does something useful with data.

**Two types of parsers:**
1. **SAX** (Simple API for XML)
2. **DOM** (Document Object Model)

---

### SAX (Simple API for XML)

**Characteristics:**
- Ad-hoc (but very popular) standard
- Developed by David Megginson, open source
- Used when document is large and device is memory constrained
- Best when need to modify document (SAX doesn't remember previous events unless write explicit code)
- Supported languages: Java, Perl, C++, Python
- Works through **callbacks** - we call parser, it calls methods we supply

**When to use SAX:**
- Large documents
- Limited memory
- Don't need to modify document
- One-pass processing

---

### DOM (Document Object Model)

**What is DOM?**

Platform and language-neutral interface that allows programs and scripts to dynamically access and update content, structure, and style of document.

**DOM is W3C standard** separated into 3 parts:
- **Core DOM**: Standard object model for all document elements
- **XML DOM**: Standard object model for XML
- **HTML DOM**: Standard object model for HTML

DOM defines objects and properties of all document elements and methods to access them.

---

**HTML DOM**

Standard object model for HTML and standard programming interface to HTML.

HTML DOM defines:
- Objects and properties of all HTML elements
- Methods to access them

In other words, **HTML DOM is standard for how to get, change, add or delete HTML**.

---

**DOM Nodes**

According to DOM:
- Entire document is **document node**
- Every HTML element is **element node**
- Text in HTML elements are **text nodes**
- HTML attributes is **attribute node**
- Comments are **comment nodes**

---

**HTML DOM Node Tree Example:**

```html
<html>
<head>
    <title>DOM</title>
</head>
<body>
    <h1>lesson 1</h1>
    <p>Hello World</p>
</body>
</html>
```

**Tree Structure:**
```
Document
└─ Root Element <html>
   ├─ Element <head>
   │  └─ Element <title>
   │     └─ Text "My title"
   └─ Element <body>
      ├─ Element <h1>
      │  └─ Text "lesson 1"
      └─ Element <p>
         └─ Text "Hello World"
```

**Node Relationships:**
- Top node = **root**
- Every node has exactly one parent (except root)
- Node can have any number of children
- Leaf = node with no children
- Siblings = nodes with same parent

---

**HTML DOM Properties**

Important properties:
- `innerHTML` – text value of X
- `nodeName` – name of X
- `nodeValue` – value of X
- `parentNode` – parent nodes of X
- `childNodes` – child nodes of X
- `attributes` – attributes nodes of X

---

**HTML DOM Methods**

Important methods:
- `getElementById(id)` – get element with special id
- `getElementsByTagName(name)` – get all elements with specified tag name
- `appendChild(node)` – insert child node from X
- `removeChild(node)` – remove child node from X

*In the list above, X is a node object.*

---

**innerHTML Property**

Useful for returning or replacing content of HTML elements. Can also be used to view source of page that has been dynamically modified.

**Example:**

```html
<html>
<body>
    <p id="demo">Hello World!</p>
    <script type="text/javascript">
        document.getElementById("demo").innerHTML = "Paragraph changed!";
    </script>
</body>
</html>
```

**Output:** "Paragraph changed!" (original text replaced)

---

**Accessing Nodes - Three Ways:**

**1. Using getElementById() method:**
```javascript
node.getElementById("id");
```

**2. Using getElementsByTagName() method:**
```javascript
node.getElementsByTagName("tagname");
```

**3. Navigating Node tree using node relationships:**

**Example HTML:**
```html
<html>
<body>
    <p>Example list:</p>
    <ul id="myList">
        <li>Coffee</li>
        <li>Tea</li>
    </ul>
    <button onclick="myFunction()">Try it</button>
</body>
</html>
```

**JavaScript:**
```javascript
function myFunction() {
    var list = document.getElementById("myList").firstChild.innerHTML;
    document.getElementById("demo").innerHTML = list;
}
```

**Explanation:**
- Gets element with id="myList"
- `.firstChild` gets first `<li>` element
- `.innerHTML` gets its text content
- Result displayed in element with id="demo"

---

**Whitespace Issue in DOM:**

**Example:**
```html
<p><strong>Note:</strong> Whitespace inside elements is considered as text, and text is considered as nodes.</p>
<p>If you add whitespace before the first LI element, the result will be "undefined".</p>
<p id="demo"></p>
<script>
function myFunction() {
    var list = document.getElementById("myList").firstChild.innerHTML;
    document.getElementById("demo").innerHTML = list;
}
</script>
```

**Issue:** If add whitespace before first `<li>`, `firstChild` will be text node (whitespace), and result will be "undefined".

---

**Changing HTML Element Example:**

```html
<html>
<body>
    <p id="P1">Hello World!</p>
    <script type="text/javascript">
        document.getElementById("P1").innerHTML = "World!";
    </script>
</body>
</html>
```

**Before:** Hello World!  
**After:** World!

---

**Example with Multiple Paragraphs:**

```html
<html>
<body>
    <p>Click the button to change the text of this paragraph.</p>
    <p>This is also a paragraph.</p>
    <button onclick="myFunction()">Try it</button>
    <script>
    function myFunction() {
        document.getElementsByTagName("P")[0].innerHTML = "Hello World!";
    }
    </script>
</body>
</html>
```

**Explanation:**
- `getElementsByTagName("P")` returns array of all `<p>` elements
- `[0]` selects first paragraph
- Only first paragraph text changes to "Hello World!"

---

**Changing HTML Elements - Summary**

HTML DOM and JavaScript can change inner element and attributes of HTML elements.

**Example:**
```html
<html>
<body>
    <script type="text/javascript">
        document.body.style.backgroundColor = "red";
        //document.body.bgcolor="red";
    </script>
</body>
</html>
```

**Result:** Background color changes to red

---

**Another Example:**

```html
<html>
<body>
    <p id="P1">Hello!</p>
    <script type="text/javascript">
        document.getElementById("P1").innerHTML= "World!";
    </script>
</body>
</html>
```

---

**Copying Content Between Elements:**

```html
<html>
<body>
    <h1 id="id01">My First Page</h1>
    <p id="id02"></p>
    
    <script>
    document.getElementById("id02").innerHTML = document.getElementById("id01").innerHTML;
    </script>
</body>
</html>
```

**Result:** Content of `<h1>` ("My First Page") copied to `<p>`

---

### XML DOM

**What is XML DOM?**

Standard model for XML and standard programming interface for XML. It's platform and language-independent.

XML DOM defines:
- Objects and properties of all XML elements
- Methods to access them

In other words, **XML DOM is standard for how to get, change, add or delete XML elements**.

---

**XML DOM Nodes**

According to DOM, everything in XML document is a node:
- Entire document is **document node**
- Every HTML element is **element node**
- Text in HTML elements are **test nodes**
- Every attribute is **attribute node**
- Comments are **comment nodes**

---

**XML DOM Node Tree**

XML DOM views HTML document as tree structure (node tree). All nodes can be accessed through tree. Contents can be modified or deleted, and new elements can be created.

**Tree Structure:**
- Starts at root node
- Branches out to text nodes at lowest level of tree

---

**Example XML Structure:**

```
Root element
<bookstore>
├─ Parent ┬ Child ─ Element <title>
│         │        Attribute "lang"
│         │        └─ Text "Italian"
│         ├─ Sibling ─ Element <author>
│         │           └─ Text "Fam"
│         ├─ Sibling ─ Element <year>
│         │           └─ Text "2005"
│         └─ Sibling ─ Element <price>
│                     └─ Text "30.00"
└─ Element tree diagram shown
```

---

**HTML DOM Properties (for XML)**

- `nodeName` – name of X
- `nodeValue` – value of X  
- `parentNode` – parent nodes of X
- `childNodes` – child nodes of X
- `attributes` – attributes nodes of X

---

**HTML DOM Methods (for XML)**

- `getElementsByTagName(name)` – get all elements with specified tag name
- `appendChild(node)` – insert child node from X
- `removeChild(node)` – remove child node from X

*X is node object*

---

**getElementsByTagName() Method**

Returns all elements with specified tag name.

**Syntax:**
```javascript
node.getElementsByTagName("tagname");
```

**Example:**

Following example returns all `<title>` elements under X element:

```javascript
X.getElementsByTagName("title");
```

---

**To remove all `<title>` elements:**

```javascript
xmlDoc.getElementsByTagName("title");
```

---

**DOM Node List**

The `getElementsByTagName()` method returns **node list**. Node list is array of nodes.

**Example - Load "books.xml" into xmlDoc:**

```javascript
xmlDoc = loadXMLDoc("books.xml");

X = xmlDoc.getElementsByTagName("title");
```

`<title>` elements in X can be accessed by index number. To access third `<title>`, write:

```javascript
T = X[2]
```

---

**DOM Node list Length**

Length property defines length of node list. Can loop through node list by using length property.

**Example:**

```javascript
xmlDoc=loadXMLDoc("books.xml");

x=xmlDoc.getElementsByTagName("title");
for (i=0; i<x.length; i++) {
    document.write(x[i].childNodes[0].nodeValue);
    document.write("<br />");
}
```

**Explanation:**
1. Load "books.xml" into xmlDoc using `LoadXMLDoc()`
2. Get text node of first `<title>` element node
3. Set txt variable to be value of text node

---

**Node Properties**

In XML DOM, each node is an object. Objects have methods and properties that can be accessed and manipulated by JavaScript.

**Three important node properties:**
- `nodeName`
- `nodeValue`
- `nodeType`

---

**Get the value of an Element**

Following code retrieves text node value of first `<title>` element.

**Example:**

```javascript
xmlDoc = loadXMLDoc("books.xml");

X = xmlDoc.getElementsByTagName("title") [0]. childNodes[0];

Txt = X.nodeValue;
```

Then:

**Result:**
```
Txt = "Italian"
```

**Example Explained:**
1. Load "books.xml" into xmlDoc
2. Get text node of first `<title>` element node
3. Set txt variable to value of text node

---
