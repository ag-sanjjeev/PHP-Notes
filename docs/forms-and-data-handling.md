## &#10162; Forms and Data Handling:

### &#9780; Overview:
1. [Creating Forms](#-creating-forms)
2. [Handling Forms](#-handling-forms)
3. [Processing Data](#-processing-data)
4. [Input Validation](#-input-validation)
5. [Input Sanitization](#-input-sanitization)
6. [Filter Variable Flags](#-filter-variable-flags)

### &#10022; Creating Forms:
Creating HTML forms with action and method. Which are used to collect user input and required data.
*Example:*
```html
<form action="process.php" method="post">
  <label for="name">Name:</label>
  <input type="text" id="name" name="name"><br>
  <label for="email">Email:</label>
  <input type="email" id="email" name="email"><br>
  <button type="submit">Submit</button>
</form>
```

### &#10022; Handling Forms:
After the form submission, the user input or data need to be handled properly. First that data needs to be validated then sanitized further process.

*Example:*
```php
if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    $name = $_POST['name'];
    $email = $_POST['email'];

    // Process the data, e.g., store in a database, send an email
    echo "Name: " . $name . "<br>";
    echo "Email: " . $email;
}
```

### &#10022; Processing Data:
Once the form data validated sanitized then it can be processed in various ways:
- Storing or updating data in a Database,
- Sending an response or email,
- Redirecting to another page.

### &#10022; Input Validation:
Input or Data validation ensures that user input or data meets specific criteria and is in the correct and required format.

*Techniques:*
- Client-Side Validation:
	- `HTML5 Form Validation`: use attributes like `accept`, `required`, `pattern`, `min`, `max`, etc., to enforce basic validation rules before form submit.
	- `JavaScript`: use functions or logic to validate input before it's sent to the server.

- Regular Expressions: helps to match specific patterns.
   ```php
   if (preg_match("/^[a-zA-Z ]+$/", $_POST['name'])) {
       // Name is valid
   }
   ```
- Built-in Validation Functions:
   - `is_numeric()`: Checks if a variable is numeric.
   - `is_int()`: Checks if a variable is an integer.
   - `is_float()`: Checks if a variable is a float.
   - `is_string()`: Checks if a variable is a string.
   - `ctype_alpha()`: Checks if a string contains only alphabetic characters.
   - `is_array()`: Checks if a variable is an array.
   - `is_bool()`: Checks if a variable is a boolean.
- Custom Validation Functions: custom functions to validate specific requirements, such as password strength or email format.
```php
function validateForm() {
    $name = trim($_POST['name']);
    $email = filter_var($_POST['email'], FILTER_VALIDATE_EMAIL);
    $password = $_POST['password'];

    if (empty($name) || empty($email) || empty($password)) {
        echo "Please fill all the fields.";
    } elseif (!filter_var($email, FILTER_VALIDATE_EMAIL)) {
        echo "Invalid email address.";
    } elseif (strlen($password) < 8) {
        echo "Password must be at least 8 characters.";
    } else {
        // Process the form data
    }
}
```

### &#10022; Input Sanitization:
Input or Data sanitization involves cleaning and filtering data to remove harmful or malicious code or unwanted part from it.

*Techniques:*
- `trim()`: Removes whitespace from the beginning and end of a string.
```php
$name = trim($_POST['name']);
```
- `strip_tags()`: Removes HTML and PHP tags from a string.
```php
$comment = strip_tags($_POST['comment']);
```
- `htmlspecialchars()`: Converts special characters into HTML entities.
```php
$message = htmlspecialchars($_POST['message']);
```
- `filter_var()`: Filters a variable with a specified filteration.
```php
$email = filter_var($_POST['email'], FILTER_VALIDATE_EMAIL);
```
- `prepared statements`: Secure approach to prevent SQL injections when working with databases.
```php
// Method 1
$statement = $pdo->prepare("INSERT INTO users (name, email) VALUES (?, ?)");
$statement->execute([$sanitized_name, $sanitized_email]);

// Method 2
$statement = $pdo->prepare("INSERT INTO users (name, email) VALUES (:name, :email)");
$statement->execute(array(':name' => $sanitized_name, ':email' => $sanitized_email));
```

### &#10022; Filter Variable Flags:

- `FILTER_VALIDATE_INT`: Validates an integer.
  ```php
  $int_value = filter_var("123dfg", FILTER_VALIDATE_INT);
  ```
- `FILTER_VALIDATE_FLOAT`: Validates a floating-point number.
  ```php
  $float_value = filter_var("3.14abc", FILTER_VALIDATE_FLOAT);
  ```
- `FILTER_VALIDATE_BOOL`: Validates a boolean.
  ```php
  $bool_value = filter_var("1", FILTER_VALIDATE_BOOL);
  ```
- `FILTER_VALIDATE_URL`: Validates a URL.
  ```php
  $url_value = filter_var("http://example.com/script?param=value", FILTER_VALIDATE_URL);
  ```
- `FILTER_VALIDATE_EMAIL`: Validates an email address.
  ```php
  $email_value = filter_var("user@example.com\n", FILTER_VALIDATE_EMAIL);
  ```
- `FILTER_VALIDATE_IP`: Validates an IP address.
  ```php
  $ip_value = filter_var("192.168.1.1", FILTER_VALIDATE_IP);
  ```
- `FILTER_SANITIZE_STRING`: Removes tags and extra whitespace.
  ```php
  $sanitized_string = filter_var("<p>Hello, world!</p>", FILTER_SANITIZE_STRING);
  ```
- `FILTER_SANITIZE_SPECIAL_CHARS`: Encodes special characters.
  ```php
  $sanitized_string = filter_var("<script>alert('XSS')</script>", FILTER_SANITIZE_SPECIAL_CHARS);
  ```
- Additional Flags:
	- `FILTER_FLAG_ALLOW_FRACTION`: Allows fractional numbers for FILTER_VALIDATE_FLOAT.
	- `FILTER_FLAG_ALLOW_THOUSAND`: Allows thousands separators for numbers.
	- `FILTER_FLAG_ALLOW_SCIENTIFIC`: Allows scientific notation.
	- `FILTER_FLAG_NO_ENCODE_QUOTES`: Prevents encoding of single and double quotes.

---
[&#8682; To Top](#-forms-and-data-handling)

[&#10094; Previous Topic](./super-globals.md) &emsp; [Next Topic &#10095;](./headers.md)

[&#8962; Goto Home Page](../README.md)