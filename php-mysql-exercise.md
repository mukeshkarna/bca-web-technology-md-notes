# PHP and MySQL Lab Practice Exercises

## Level 1: PHP Basics

### Exercise 1: PHP Fundamentals

1. **Hello World Program**
   - Display "Welcome to PHP Programming"
   - Show current date and time using `date()` function
   - Display day of the week

2. **Variable Operations**
   - Create variables for name, age, city
   - Display them using `echo`
   - Perform arithmetic operations (add, subtract, multiply, divide)
   - Display results

3. **Comment Practice**
   - Write a program with single-line comments
   - Write a program with multi-line comments
   - Document your code properly

### Exercise 2: Control Structures

1. **If-Else Statements**
   - Check if a number is even or odd
   - Check if a person is eligible to vote (age >= 18)
   - Find the largest of three numbers

2. **Switch Case**
   - Create a simple calculator (+, -, *, /)
   - Display day name based on day number (1-7)
   - Display grade based on marks (A, B, C, D, F)

3. **Loops - For Loop**
   - Print numbers 1 to 10
   - Print multiplication table of any number
   - Print even numbers from 1 to 20

4. **Loops - While Loop**
   - Print numbers 10 to 1 (reverse order)
   - Calculate factorial of a number
   - Sum of first 10 natural numbers

5. **Loops - Foreach**
   - Create an array of 5 fruits and display them
   - Create an associative array of student names and marks, display them
   - Create array of colors and display with serial numbers

---

## Level 2: Functions and Forms

### Exercise 3: Functions

1. **Simple Functions**
   - Create a function to add two numbers
   - Create a function to check if number is prime
   - Create a function to reverse a string

2. **Functions with Return Values**
   - Function to calculate area of circle
   - Function to calculate simple interest
   - Function to find maximum of three numbers

3. **Built-in Functions**
   - Use `strlen()`, `strrev()`, `strtoupper()`, `strtolower()`
   - Use `substr()`, `str_replace()`
   - Use `explode()`, `implode()`

### Exercise 4: Form Handling

1. **Simple Form Processing**
   ```html
   <!-- Create login.html -->
   <form method="POST" action="login.php">
       Username: <input type="text" name="username"><br>
       Password: <input type="password" name="password"><br>
       <input type="submit" value="Login">
   </form>
   ```
   ```php
   <!-- login.php -->
   <?php
   $username = $_POST['username'];
   $password = $_POST['password'];
   echo "Welcome $username";
   ?>
   ```

2. **Registration Form**
   - Create form with: First Name, Last Name, Email, Phone, Gender (radio), City (dropdown)
   - Display all submitted data on next page

3. **Calculator Form**
   - Create form with two numbers and operation dropdown
   - Perform calculation and display result

### Exercise 5: Form Validation

1. **Basic Validation**
   - Create registration form
   - Check all fields are filled (required field validation)
   - Validate email format using `preg_match()`
   - Validate phone number (10 digits only)

2. **Advanced Validation**
   ```php
   function validate_input($data) {
       $data = trim($data);
       $data = stripslashes($data);
       $data = htmlspecialchars($data);
       return $data;
   }
   ```
   - Apply to all form inputs
   - Check password length (minimum 6 characters)
   - Validate age (should be number between 18-60)

---

## Level 3: Sessions and Cookies

### Exercise 6: Session Management

1. **Simple Login System**
   ```php
   <!-- login.php -->
   <?php
   session_start();
   if($_POST['username'] == 'admin' && $_POST['password'] == '123') {
       $_SESSION['username'] = $_POST['username'];
       header('Location: dashboard.php');
   } else {
       echo "Invalid credentials";
   }
   ?>
   ```

   ```php
   <!-- dashboard.php -->
   <?php
   session_start();
   if(!isset($_SESSION['username'])) {
       header('Location: login.php');
       exit();
   }
   echo "Welcome " . $_SESSION['username'];
   ?>
   ```

   ```php
   <!-- logout.php -->
   <?php
   session_start();
   session_destroy();
   header('Location: login.php');
   ?>
   ```

2. **Shopping Cart using Sessions**
   - Add items to cart
   - Display cart items
   - Remove items from cart
   - Calculate total price

3. **Page View Counter**
   - Count how many times user visited the page
   - Display visit count

### Exercise 7: Cookie Management

1. **Remember Me Feature**
   ```php
   // Set cookie for 30 days
   setcookie("username", $username, time() + (86400 * 30), "/");
   
   // Check if cookie exists
   if(isset($_COOKIE['username'])) {
       echo "Welcome back " . $_COOKIE['username'];
   }
   ```

2. **User Preference**
   - Store user's preferred theme (light/dark) in cookie
   - Display page according to preference

3. **Last Visit Tracker**
   - Store last visit date/time in cookie
   - Display on next visit

---

## Level 4: File Handling

### Exercise 8: File Operations

1. **Write to File**
   ```php
   <?php
   $file = fopen("data.txt", "w");
   $text = "Hello World!\n";
   fwrite($file, $text);
   fclose($file);
   echo "Data written to file";
   ?>
   ```

2. **Read from File**
   ```php
   <?php
   $file = fopen("data.txt", "r");
   while(!feof($file)) {
       echo fgets($file) . "<br>";
   }
   fclose($file);
   ?>
   ```

3. **Append to File**
   - Create a guestbook where users can add messages
   - Store messages in text file (append mode)
   - Display all messages

4. **File Upload**
   ```html
   <form method="POST" enctype="multipart/form-data">
       <input type="file" name="file">
       <input type="submit" value="Upload">
   </form>
   ```
   ```php
   <?php
   $target_dir = "uploads/";
   $target_file = $target_dir . basename($_FILES["file"]["name"]);
   
   if(move_uploaded_file($_FILES["file"]["tmp_name"], $target_file)) {
       echo "File uploaded successfully";
   } else {
       echo "Error uploading file";
   }
   ?>
   ```

---

## Level 5: Database Connectivity

### Exercise 9: MySQL Database Setup

1. **Create Database and Table**
   ```sql
   CREATE DATABASE college;
   USE college;
   
   CREATE TABLE students (
       id INT(6) AUTO_INCREMENT PRIMARY KEY,
       name VARCHAR(50) NOT NULL,
       email VARCHAR(50) NOT NULL,
       phone VARCHAR(15),
       address VARCHAR(100),
       created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
   );
   ```

2. **Database Connection**
   ```php
   <?php
   // config.php
   $servername = "localhost";
   $username = "root";
   $password = "";
   $dbname = "college";
   
   $conn = mysqli_connect($servername, $username, $password, $dbname);
   
   if(!$conn) {
       die("Connection failed: " . mysqli_connect_error());
   }
   echo "Connected successfully";
   ?>
   ```

---

## Level 6: CRUD Operations

### Exercise 10: CREATE Operation (Insert Data)

**Task: Student Registration System**

1. **Create HTML Form (register.html)**
   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <title>Student Registration</title>
       <style>
           body {
               font-family: Arial, sans-serif;
               max-width: 500px;
               margin: 50px auto;
               padding: 20px;
               background-color: #f4f4f4;
           }
           form {
               background: white;
               padding: 20px;
               border-radius: 8px;
           }
           input[type="text"], input[type="email"], textarea {
               width: 100%;
               padding: 8px;
               margin: 8px 0;
               border: 1px solid #ddd;
               border-radius: 4px;
           }
           input[type="submit"] {
               background-color: #4CAF50;
               color: white;
               padding: 10px 20px;
               border: none;
               border-radius: 4px;
               cursor: pointer;
           }
           input[type="submit"]:hover {
               background-color: #45a049;
           }
           .error {
               color: red;
               font-size: 14px;
           }
       </style>
   </head>
   <body>
       <h2>Student Registration Form</h2>
       <form method="POST" action="insert.php">
           <label>Name:</label>
           <input type="text" name="name" required>
           
           <label>Email:</label>
           <input type="email" name="email" required>
           
           <label>Phone:</label>
           <input type="text" name="phone" required>
           
           <label>Address:</label>
           <textarea name="address" rows="4" required></textarea>
           
           <input type="submit" value="Register">
       </form>
   </body>
   </html>
   ```

2. **Create Insert Script (insert.php)**
   ```php
   <?php
   include 'config.php';
   
   if($_SERVER["REQUEST_METHOD"] == "POST") {
       // Validate and sanitize input
       $name = mysqli_real_escape_string($conn, $_POST['name']);
       $email = mysqli_real_escape_string($conn, $_POST['email']);
       $phone = mysqli_real_escape_string($conn, $_POST['phone']);
       $address = mysqli_real_escape_string($conn, $_POST['address']);
       
       // Validate email
       if(!filter_var($email, FILTER_VALIDATE_EMAIL)) {
           echo "Invalid email format";
           exit();
       }
       
       // Insert query
       $sql = "INSERT INTO students (name, email, phone, address) 
               VALUES ('$name', '$email', '$phone', '$address')";
       
       if(mysqli_query($conn, $sql)) {
           echo "<h3>Student registered successfully!</h3>";
           echo "<a href='display.php'>View All Students</a>";
       } else {
           echo "Error: " . $sql . "<br>" . mysqli_error($conn);
       }
   }
   
   mysqli_close($conn);
   ?>
   ```

**Practice Tasks:**
- Add validation for phone number (exactly 10 digits)
- Check if email already exists before inserting
- Display success message with proper styling
- Add a "Back to Form" button

---

### Exercise 11: READ Operation (Display Data)

**Task: Display All Students**

1. **Display All Records (display.php)**
   ```php
   <?php
   include 'config.php';
   ?>
   
   <!DOCTYPE html>
   <html>
   <head>
       <title>Student List</title>
       <style>
           body {
               font-family: Arial, sans-serif;
               margin: 20px;
           }
           table {
               width: 100%;
               border-collapse: collapse;
               margin-top: 20px;
           }
           th, td {
               border: 1px solid #ddd;
               padding: 12px;
               text-align: left;
           }
           th {
               background-color: #4CAF50;
               color: white;
           }
           tr:nth-child(even) {
               background-color: #f2f2f2;
           }
           tr:hover {
               background-color: #ddd;
           }
           .action-btn {
               padding: 5px 10px;
               margin: 2px;
               text-decoration: none;
               color: white;
               border-radius: 3px;
           }
           .edit-btn {
               background-color: #2196F3;
           }
           .delete-btn {
               background-color: #f44336;
           }
       </style>
   </head>
   <body>
       <h2>Student List</h2>
       <a href="register.html">Add New Student</a>
       
       <table>
           <tr>
               <th>ID</th>
               <th>Name</th>
               <th>Email</th>
               <th>Phone</th>
               <th>Address</th>
               <th>Registered Date</th>
               <th>Actions</th>
           </tr>
           
           <?php
           $sql = "SELECT * FROM students ORDER BY id DESC";
           $result = mysqli_query($conn, $sql);
           
           if(mysqli_num_rows($result) > 0) {
               while($row = mysqli_fetch_assoc($result)) {
                   echo "<tr>";
                   echo "<td>" . $row['id'] . "</td>";
                   echo "<td>" . $row['name'] . "</td>";
                   echo "<td>" . $row['email'] . "</td>";
                   echo "<td>" . $row['phone'] . "</td>";
                   echo "<td>" . $row['address'] . "</td>";
                   echo "<td>" . $row['created_at'] . "</td>";
                   echo "<td>
                           <a href='edit.php?id=" . $row['id'] . "' class='action-btn edit-btn'>Edit</a>
                           <a href='delete.php?id=" . $row['id'] . "' class='action-btn delete-btn' onclick='return confirm(\"Are you sure?\")'>Delete</a>
                         </td>";
                   echo "</tr>";
               }
           } else {
               echo "<tr><td colspan='7'>No students found</td></tr>";
           }
           
           mysqli_close($conn);
           ?>
       </table>
   </body>
   </html>
   ```

2. **Display Single Record (view.php)**
   ```php
   <?php
   include 'config.php';
   
   $id = $_GET['id'];
   $sql = "SELECT * FROM students WHERE id = $id";
   $result = mysqli_query($conn, $sql);
   
   if(mysqli_num_rows($result) == 1) {
       $row = mysqli_fetch_assoc($result);
   ?>
   
   <!DOCTYPE html>
   <html>
   <head>
       <title>Student Details</title>
       <style>
           .detail-box {
               max-width: 500px;
               margin: 50px auto;
               padding: 20px;
               border: 1px solid #ddd;
               border-radius: 8px;
           }
           .detail-row {
               padding: 10px;
               border-bottom: 1px solid #eee;
           }
           .label {
               font-weight: bold;
               display: inline-block;
               width: 150px;
           }
       </style>
   </head>
   <body>
       <div class="detail-box">
           <h2>Student Details</h2>
           <div class="detail-row">
               <span class="label">ID:</span>
               <span><?php echo $row['id']; ?></span>
           </div>
           <div class="detail-row">
               <span class="label">Name:</span>
               <span><?php echo $row['name']; ?></span>
           </div>
           <div class="detail-row">
               <span class="label">Email:</span>
               <span><?php echo $row['email']; ?></span>
           </div>
           <div class="detail-row">
               <span class="label">Phone:</span>
               <span><?php echo $row['phone']; ?></span>
           </div>
           <div class="detail-row">
               <span class="label">Address:</span>
               <span><?php echo $row['address']; ?></span>
           </div>
           <div class="detail-row">
               <span class="label">Registered:</span>
               <span><?php echo $row['created_at']; ?></span>
           </div>
           <br>
           <a href="display.php">Back to List</a>
       </div>
   </body>
   </html>
   
   <?php
   } else {
       echo "Student not found";
   }
   mysqli_close($conn);
   ?>
   ```

**Practice Tasks:**
- Add search functionality (search by name or email)
- Add pagination (display 10 records per page)
- Add sorting (sort by name, email, date)
- Add "View Details" button in the table

---

### Exercise 12: UPDATE Operation (Edit Data)

**Task: Edit Student Information**

1. **Edit Form (edit.php)**
   ```php
   <?php
   include 'config.php';
   
   $id = $_GET['id'];
   $sql = "SELECT * FROM students WHERE id = $id";
   $result = mysqli_query($conn, $sql);
   $row = mysqli_fetch_assoc($result);
   ?>
   
   <!DOCTYPE html>
   <html>
   <head>
       <title>Edit Student</title>
       <style>
           body {
               font-family: Arial, sans-serif;
               max-width: 500px;
               margin: 50px auto;
               padding: 20px;
               background-color: #f4f4f4;
           }
           form {
               background: white;
               padding: 20px;
               border-radius: 8px;
           }
           input[type="text"], input[type="email"], textarea {
               width: 100%;
               padding: 8px;
               margin: 8px 0;
               border: 1px solid #ddd;
               border-radius: 4px;
           }
           input[type="submit"] {
               background-color: #2196F3;
               color: white;
               padding: 10px 20px;
               border: none;
               border-radius: 4px;
               cursor: pointer;
           }
           input[type="submit"]:hover {
               background-color: #0b7dda;
           }
       </style>
   </head>
   <body>
       <h2>Edit Student Information</h2>
       <form method="POST" action="update.php">
           <input type="hidden" name="id" value="<?php echo $row['id']; ?>">
           
           <label>Name:</label>
           <input type="text" name="name" value="<?php echo $row['name']; ?>" required>
           
           <label>Email:</label>
           <input type="email" name="email" value="<?php echo $row['email']; ?>" required>
           
           <label>Phone:</label>
           <input type="text" name="phone" value="<?php echo $row['phone']; ?>" required>
           
           <label>Address:</label>
           <textarea name="address" rows="4" required><?php echo $row['address']; ?></textarea>
           
           <input type="submit" value="Update">
           <a href="display.php">Cancel</a>
       </form>
   </body>
   </html>
   
   <?php
   mysqli_close($conn);
   ?>
   ```

2. **Update Script (update.php)**
   ```php
   <?php
   include 'config.php';
   
   if($_SERVER["REQUEST_METHOD"] == "POST") {
       $id = $_POST['id'];
       $name = mysqli_real_escape_string($conn, $_POST['name']);
       $email = mysqli_real_escape_string($conn, $_POST['email']);
       $phone = mysqli_real_escape_string($conn, $_POST['phone']);
       $address = mysqli_real_escape_string($conn, $_POST['address']);
       
       // Validate email
       if(!filter_var($email, FILTER_VALIDATE_EMAIL)) {
           echo "Invalid email format";
           exit();
       }
       
       $sql = "UPDATE students SET 
               name = '$name',
               email = '$email',
               phone = '$phone',
               address = '$address'
               WHERE id = $id";
       
       if(mysqli_query($conn, $sql)) {
           echo "<h3>Student updated successfully!</h3>";
           echo "<a href='display.php'>View All Students</a>";
       } else {
           echo "Error: " . mysqli_error($conn);
       }
   }
   
   mysqli_close($conn);
   ?>
   ```

**Practice Tasks:**
- Check if email is already used by another student before updating
- Add validation for all fields
- Show old and new values comparison
- Add "Last Updated" timestamp column

---

### Exercise 13: DELETE Operation

**Task: Delete Student Record**

1. **Delete Script (delete.php)**
   ```php
   <?php
   include 'config.php';
   
   if(isset($_GET['id'])) {
       $id = $_GET['id'];
       
       // First, fetch student details before deleting
       $select_sql = "SELECT name FROM students WHERE id = $id";
       $result = mysqli_query($conn, $select_sql);
       $row = mysqli_fetch_assoc($result);
       $student_name = $row['name'];
       
       // Delete query
       $sql = "DELETE FROM students WHERE id = $id";
       
       if(mysqli_query($conn, $sql)) {
           echo "<h3>Student '$student_name' deleted successfully!</h3>";
           echo "<a href='display.php'>Back to Student List</a>";
       } else {
           echo "Error deleting record: " . mysqli_error($conn);
       }
   } else {
       echo "Invalid request";
   }
   
   mysqli_close($conn);
   ?>
   ```

2. **Delete with Confirmation (delete_confirm.php)**
   ```php
   <?php
   include 'config.php';
   
   if(isset($_GET['id'])) {
       $id = $_GET['id'];
       $sql = "SELECT * FROM students WHERE id = $id";
       $result = mysqli_query($conn, $sql);
       $row = mysqli_fetch_assoc($result);
   ?>
   
   <!DOCTYPE html>
   <html>
   <head>
       <title>Delete Confirmation</title>
       <style>
           .confirm-box {
               max-width: 500px;
               margin: 100px auto;
               padding: 30px;
               border: 2px solid #f44336;
               border-radius: 8px;
               background-color: #ffebee;
               text-align: center;
           }
           .btn {
               padding: 10px 20px;
               margin: 10px;
               border: none;
               border-radius: 4px;
               cursor: pointer;
               text-decoration: none;
               display: inline-block;
           }
           .delete-btn {
               background-color: #f44336;
               color: white;
           }
           .cancel-btn {
               background-color: #9E9E9E;
               color: white;
           }
       </style>
   </head>
   <body>
       <div class="confirm-box">
           <h2>⚠️ Delete Confirmation</h2>
           <p>Are you sure you want to delete this student?</p>
           <div style="margin: 20px 0; padding: 15px; background: white; border-radius: 4px;">
               <strong>Name:</strong> <?php echo $row['name']; ?><br>
               <strong>Email:</strong> <?php echo $row['email']; ?><br>
               <strong>Phone:</strong> <?php echo $row['phone']; ?>
           </div>
           <p style="color: red; font-weight: bold;">This action cannot be undone!</p>
           
           <form method="POST" action="delete.php">
               <input type="hidden" name="id" value="<?php echo $id; ?>">
               <input type="submit" value="Yes, Delete" class="btn delete-btn">
               <a href="display.php" class="btn cancel-btn">Cancel</a>
           </form>
       </div>
   </body>
   </html>
   
   <?php
   }
   mysqli_close($conn);
   ?>
   ```

**Practice Tasks:**
- Implement soft delete (add 'deleted' column instead of actually deleting)
- Add "Restore" functionality for soft-deleted records
- Add delete multiple records at once (using checkboxes)
- Log all delete operations in a separate table

---

## Level 7: Advanced CRUD Projects (Week 13-15)

### Project 1: Library Management System

**Database Schema:**
```sql
CREATE TABLE books (
    id INT AUTO_INCREMENT PRIMARY KEY,
    title VARCHAR(200) NOT NULL,
    author VARCHAR(100) NOT NULL,
    isbn VARCHAR(20) UNIQUE,
    category VARCHAR(50),
    quantity INT DEFAULT 1,
    available INT DEFAULT 1,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE members (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    phone VARCHAR(15),
    address TEXT,
    membership_date DATE,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE issue_records (
    id INT AUTO_INCREMENT PRIMARY KEY,
    book_id INT,
    member_id INT,
    issue_date DATE,
    return_date DATE,
    actual_return_date DATE,
    status ENUM('issued', 'returned') DEFAULT 'issued',
    FOREIGN KEY (book_id) REFERENCES books(id),
    FOREIGN KEY (member_id) REFERENCES members(id)
);
```

**Features to Implement:**
1. Book Management (Add, Edit, Delete, Search books)
2. Member Management (Register, Update, Delete members)
3. Issue Book (Select book and member, record issue date)
4. Return Book (Update return date, change status)
5. View All Issues (Current and History)
6. Search Functionality (Search books by title/author, members by name)
7. Reports (Most issued books, Overdue books, Active members)

---

### Project 2: Employee Management System

**Database Schema:**
```sql
CREATE TABLE departments (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    description TEXT
);

CREATE TABLE employees (
    id INT AUTO_INCREMENT PRIMARY KEY,
    emp_code VARCHAR(20) UNIQUE NOT NULL,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    phone VARCHAR(15),
    department_id INT,
    designation VARCHAR(50),
    salary DECIMAL(10,2),
    joining_date DATE,
    address TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (department_id) REFERENCES departments(id)
);

CREATE TABLE attendance (
    id INT AUTO_INCREMENT PRIMARY KEY,
    emp_id INT,
    date DATE,
    time_in TIME,
    time_out TIME,
    status ENUM('present', 'absent', 'half-day', 'leave'),
    FOREIGN KEY (emp_id) REFERENCES employees(id)
);
```

**Features to Implement:**
1. Department Management
2. Employee Management (CRUD operations)
3. Attendance System (Mark daily attendance)
4. Salary Calculation
5. Leave Management
6. Employee Search and Filter
7. Reports (Department-wise employees, Monthly attendance, Salary reports)

---

### Project 3: E-Commerce Product Management

**Database Schema:**
```sql
CREATE TABLE categories (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    description TEXT,
    image VARCHAR(255)
);

CREATE TABLE products (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(200) NOT NULL,
    description TEXT,
    category_id INT,
    price DECIMAL(10,2) NOT NULL,
    stock_quantity INT DEFAULT 0,
    image VARCHAR(255),
    status ENUM('active', 'inactive') DEFAULT 'active',
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (category_id) REFERENCES categories(id)
);

CREATE TABLE customers (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    phone VARCHAR(15),
    address TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE orders (
    id INT AUTO_INCREMENT PRIMARY KEY,
    customer_id INT,
    order_date DATETIME,
    total_amount DECIMAL(10,2),
    status ENUM('pending', 'confirmed', 'delivered', 'cancelled'),
    FOREIGN KEY (customer_id) REFERENCES customers(id)
);

CREATE TABLE order_items (
    id INT AUTO_INCREMENT PRIMARY KEY,
    order_id INT,
    product_id INT,
    quantity INT,
    price DECIMAL(10,2),
    FOREIGN KEY (order_id) REFERENCES orders(id),
    FOREIGN KEY (product_id) REFERENCES products(id)
);
```

**Features to Implement:**
1. Category Management
2. Product Management with Image Upload
3. Stock Management
4. Customer Registration
5. Order Processing
6. Order History
7. Sales Reports

---

### Project 4: Hospital Management System

**Database Schema:**
```sql
CREATE TABLE doctors (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    specialization VARCHAR(100),
    phone VARCHAR(15),
    email VARCHAR(100),
    schedule TEXT
);

CREATE TABLE patients (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    age INT,
    gender ENUM('male', 'female', 'other'),
    phone VARCHAR(15),
    address TEXT,
    blood_group VARCHAR(5),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE appointments (
    id INT AUTO_INCREMENT PRIMARY KEY,
    patient_id INT,
    doctor_id INT,
    appointment_date DATE,
    appointment_time TIME,
    status ENUM('scheduled', 'completed', 'cancelled'),
    symptoms TEXT,
    FOREIGN KEY (patient_id) REFERENCES patients(id),
    FOREIGN KEY (doctor_id) REFERENCES doctors(id)
);

CREATE TABLE prescriptions (
    id INT AUTO_INCREMENT PRIMARY KEY,
    appointment_id INT,
    medicines TEXT,
    instructions TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (appointment_id) REFERENCES appointments(id)
);
```

**Features to Implement:**
1. Doctor Management
2. Patient Registration
3. Appointment Booking
4. Appointment Management (View, Reschedule, Cancel)
5. Prescription Management
6. Patient History
7. Reports (Doctor-wise appointments, Patient statistics)

---

## Additional Practice Exercises

### Exercise 15: Security Best Practices

1. **Password Hashing**
   ```php
   <?php
   // Registration
   $password = $_POST['password'];
   $hashed_password = password_hash($password, PASSWORD_DEFAULT);
   
   // Store $hashed_password in database
   
   // Login
   $input_password = $_POST['password'];
   $stored_hash = // fetch from database
   
   if(password_verify($input_password, $stored_hash)) {
       echo "Login successful";
   } else {
       echo "Invalid password";
   }
   ?>
   ```

2. **Prepared Statements (SQL Injection Prevention)**
   ```php
   <?php
   // Instead of:
   $sql = "SELECT * FROM users WHERE username='$username'";
   
   // Use prepared statements:
   $stmt = $conn->prepare("SELECT * FROM users WHERE username = ?");
   $stmt->bind_param("s", $username);
   $stmt->execute();
   $result = $stmt->get_result();
   ?>
   ```

3. **CSRF Protection**
   ```php
   <?php
   // Generate token
   session_start();
   $_SESSION['csrf_token'] = bin2hex(random_bytes(32));
   
   // In form:
   echo '<input type="hidden" name="csrf_token" value="' . $_SESSION['csrf_token'] . '">';
   
   // Verify token:
   if($_POST['csrf_token'] !== $_SESSION['csrf_token']) {
       die("CSRF token validation failed");
   }
   ?>
   ```

---

## Tips for Students

1. **Practice Daily**: Spend at least 1-2 hours daily on PHP coding

2. **Understand Don't Memorize**: Focus on understanding logic rather than memorizing code

3. **Error Handling**: Always check for errors using `mysqli_error()` during development

4. **Use Comments**: Comment your code for better understanding

5. **Test Thoroughly**: Test all scenarios including edge cases

6. **Security First**: Always validate and sanitize user input

7. **Code Organization**: Keep your code organized and follow naming conventions

8. **Version Control**: Use Git to track your progress

9. **Documentation**: Maintain a lab notebook with all exercises

10. **Ask Questions**: Don't hesitate to ask when stuck

---

**Good Luck with your PHP and MySQL learning! 🚀**