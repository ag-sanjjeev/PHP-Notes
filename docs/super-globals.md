## &#10162; Super Globals:
Super globals are built-in PHP variables that are available in all scopes of the scripts. It holds and provide access to various types of information. Including form data, session data, and server environment variables.

### &#9780; Overview:
1. [GET Variable](#-get-variable)
2. [POST Variable](#-post-variable)
3. [REQUEST Variable](#-request-variable)
4. [FILES Variable](#-files-variable)
5. [SESSION Variable](#-session-variable)
6. [COOKIE Variable](#-cookie-variable)
7. [SERVER Variable](#-server-variable)
8. [ENV Variable](#-env-variable)

### &#10022; GET Variable:
It is used to collect form data sent with the GET method.

*Pros:*
- This can be bookmarked.

*Cons:*
- Limited data size.
- It is not suitable for sensitive data.
- Data is visible in the URL.

*Security Practices:*
- Sanitize and validate input to prevent attacks like XSS.

*Syntax: `$_GET['variable_name']`*

*Example:*
```php
if(isset($_GET['name'])){
  echo "Hello, " . $_GET['name'] . "!";
}
```

### &#10022; POST Variable:
It is used to collect form data sent with the POST method.

*Pros:*
- Data is not visible in the URL.
- It can handle large amounts of data.

*Cons:*
- It cannot be bookmarked.

*Security Practices:*
- Sanitize and validate input to prevent attacks like SQL injection and XSS.

*Syntax: `$_POST['variable_name']`*

*Example:*
```php
if(isset($_POST['name'])){
  echo "Hello, " . $_POST['name'] . "!";
}
```

### &#10022; REQUEST Variable:
It contains data from both GET and POST request methods.

*Pros:*
- It can be used to access data from both GET and POST requests.

*Cons:* 
- It is less secure than using `$_GET` and `$_POST` directly, as it can expose application to potential security risks.

*Syntax:*
```php
$name = $_REQUEST['name'];
```

### &#10022; FILES Variable:
It contains information about uploaded files after form submission.

*Pros:*
- It allows for file uploads and processing.

*Cons:* 
- It requires careful handling to prevent security vulnerabilities.

*Security Practices:*
- Validate and filters the file before and after upload. In order to, avoid any malicious file on the server. 

*Syntax:*
```php
$filename = $_FILES['file']['name'];
$tmp_name = $_FILES['file']['tmp_name'];
```
*Example:*
```html
<form action="upload.php" method="POST" enctype="multipart/form-data">
    <input type="file" name="file">
    <button type="submit">Upload</button>
</form>
```

### &#10022; SESSION Variable:
It can stores data for a specific user session.

*Pros:*
- It can store large amounts of data.
- It can be used to track user sessions.

*Cons:*
- It requires session handling.
- Data is stored on the server.

*Security Practices:*
- Use strong session handling techniques to prevent session hijacking.

*Syntax: `$_SESSION['variable_name']`*

*Example:*
```php
session_start();
$_SESSION['user_name'] = 'Kumar';
```

### &#10022; COOKIE Variable:
It can stores data on the user's computer.

*Pros:*
- It can be used to store user preferences.

*Cons:*
- It can be manipulated by the user.
- It can store limited storage space.

*Security:*
- Set secure flags and expiration times for cookies.

*Syntax: `$_COOKIE['variable_name']`*

*Example:*
```php
// Cookie expires in 12 hour
setcookie("user_theme", "dark", time() + 43200); 
```

### &#10022; SERVER Variable:
It contains information about the server environment, such as headers, paths, and script locations.

*Pros:*
- It contains server informations
- Mainly used for debugging and troubleshooting purpose
- Security checks purpose such as verify that origin of requests with it

*Cons:*
- If it is not handled carefully, it will expose sensitive server information

*Security Practices:*
- Check and verify the usage of this variable, to avoid sensitive information leak

*Syntax:*
```php
// Returns server address name
$server_name = $_SERVER['SERVER_NAME']; // localhost
// Returns server software 
$server_software = $_SERVER['SERVER_SOFTWARE']; // PHP 8.1.2 Development Server
// Returns current PHP script file name
$filename = $_SERVER['PHP_SELF']; // test.php
// Returns user's ip address
$ip_address = $_SERVER['REMOTE_ADDR']; // ::1 
// Returns request method
$request_method = $_SERVER['REQUEST_METHOD']; // GET
// Returns server protocol
$server_protocol = $_SERVER['SERVER_PROTOCOL']; // HTTP/1.1
// Returns complete path of the PHP script path
$script_filename = $_SERVER['SCRIPT_FILENAME']; // C:\xampp\htdocs\test.php
```

### &#10022; ENV Variable:
It contains an associative array of variables passed to the script via the environment. These are set outside the PHP script, typically by the web server or operating system.

*Pros:*
- These are not directly exposed in the source code.
- It can easily change environment variables without modifying the script itself.
- It often used for configuration settings, allowing to switch between different environments (e.g., development, staging, production).

*Cons:*
- It might not be available in all environments, especially when running scripts locally.
- Managing environment variables become complex in large-scale applications.

*Security Practices:*
- Avoid storing highly sensitive information like API keys or passwords directly in environment variables. Consider, more secure methods like configuration files or secrets management tools.
- Ensure that only accessible to authorized users or processes.
- Keep system and libraries up-to-date to address security vulnerabilities related to environment variable handling.

*Example:*
```php
// Assuming the DATABASE_URL is set to "mysql://user:password@host/database"
$dbUrl = $_ENV['DATABASE_URL'];

// Parse the database URL
$dbConfig = parse_url($dbUrl);

// Connect to the database with PDO
$dsn = "mysql:host={$dbConfig['host']};dbname={$dbConfig['path']}";
$pdo = new PDO($dsn, $dbConfig['user'], $dbConfig['pass']);
```

---
[&#8682; To Top](#-super-globals)

[&#10094; Previous Topic](./short-hand-syntax.md) &emsp; [Next Topic &#10095;](./forms-and-data-handling.md)

[&#8962; Goto Home Page](../README.md)