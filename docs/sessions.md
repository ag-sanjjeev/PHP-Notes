## &#10162; Sessions:
A session is a way to store information about a user interaction with a website across multiple page requests. It allows to maintain information and state between requests, such as user preferences, login status, or temporary items such as a shopping cart, a wish list.

### &#9780; Overview:
1. [Need and Usage](#-need-and-usage)
2. [Creating Session](#-creating-session)
3. [Storing Data in Session](#-storing-data-in-session)
4. [Retrieving Data from Session](#-retrieving-data-from-session)
5. [Removing Session Data](#-removing-session-data)
6. [Destroying Session](#-destroying-session)
7. [Pros](#-pros)
8. [Cons](#-cons)
9. [Functions Related To Session](#-functions-related-to-session)
10. [Constants Related To Session](#-constants-related-to-session)
11. [Configuration Flags Related To Session](#-configuration-flags-related-to-session)
12. [Different Session Handling Techniques](#-different-session-handling-techniques)
13. [Secure Session Handling](#-secure-session-handling)
14. [Strong Session Name](#-strong-session-name)
15. [Session Handlers](#-session-handlers)
16. [Example For Custom Session Handlers](#-example-for-custom-session-handlers)
17. [Protecting Against Session Fixation](#-protecting-against-session-fixation)

### &#10022; Need and Usage:
- Authentication and Authorization: Keep track of user login status and permissions.
- Personalized Experience: Tailor the website content and layout based on the user preferences.
- Temporary Items: Maintain a user wish such as a shopping cart items.
- User Tracking: Keep track of a user activity across multiple pages.

### &#10022; Creating Session:
To create session in PHP by start a session, this initiates a session and associates it with the current user browser.

```php
session_start();
```

### &#10022; Storing Data In Session:
To store data in the session using, `$_SESSION` [super global](./super-globals.md):

```php
$_SESSION['username'] = 'Kumar';
$_SESSION['user_id'] = 64156487876;
```

### &#10022; Retrieving Data From Session:
To Access the stored data in session using, `$_SESSION` [super global](./super-globals.md):

```php
echo "Welcome, " . $_SESSION['username'];
```

### &#10022; Removing Session Data:
To remove data from session use, `unset()` function:

```php
unset($_SESSION['username']);
```

### &#10022; Destroying Session:
To destroy session use, `session_destroy()` function:

```php
session_destroy();
```

But before destroying session, That require some important steps for secure session destruction. First, Empty or clean the session array variable. Second, Remove session cookie for the current session. Finally, use `session_destroy()` function.
```php
// mention the session_name("name") if initially, it was created.
// start session
session_start();

// Unset the session array
$_SESSION = array();

// If it need to destroy the session, then it required to delete the session cookie as well.
// It removes cookie related to current session
if (ini_get("session.use_cookies")) {
    $params = session_get_cookie_params();
    setcookie(session_name(), '', time() - 42000,
        $params["path"], $params["domain"],
        $params["secure"], $params["httponly"]
    );
}

// Finally, destroy the session
session_destroy();
```

### &#10022; Pros:
 - User Tracking
 - Personalized Experience
 - Secure Authentication

### &#10022; Cons:
 - Security Risks: If session is not handled properly, then it can be vulnerable to attacks like session hijacking.
 - Performance Overhead: Sessions can add overhead to the application, especially for large-scale applications make some difference.

### &#10022; Functions Related To Session:
- `session_start()`: Initiates a new session or resumes an existing one.
- `session_regenerate_id()`: Regenerates the session ID.
- `session_name()`: Gets or sets the session name.
- `session_id()`: Gets or sets the session ID.
- `session_save_path()`: Gets or sets the session save path.
- `session_cache_limiter()`: Sets the session cache limiter.
- `session_cache_expire()`: Sets the session cache expire time.
- `session_unset()`: Removes all session variables.
- `session_destroy()`: Destroys the current session.

### &#10022; Constants Related To Session:
- `SID`: Constants that contains the session ID.

### &#10022; Configuration Flags Related To Session:
- `session.auto_start`: Determines if the session is automatically started at the beginning of each script.
- `session.name`: Sets the session name.
- `session_save_path`: Sets the directory path where session data is stored.
- `session.cookie_path`: Sets the path for the session cookie.
- `session.cookie_domain`: Sets the domain for the session cookie.
- `session.cookie_secure`: Sets whether the session cookie should only be transmitted over HTTPS.
- `session.cookie_lifetime`: Sets the expiry time of the session cookie in seconds.
- `session.use_only_cookies`: Prevents the session ID transmission through URL parameters.

### &#10022; Different Session Handling Techniques
- Built-in PHP Session Handling:
   - Simple to use and widely supported.
   - Configure session settings using `session_start()` and `session_set_cookie_params()`.

- Database based Sessions Handling:
   - More secure as session data is stored in a database.
   - Complex implementation.

- Custom Session Handling:
   - Provides greater flexibility but requires careful session handling implementation.
   - Involves storing session data in a different storage mechanism (e.g., database, file system).

### &#10022; Secure Session Handling:
```php
session_start();

// Regenerate session ID on each page load as required
session_regenerate_id(true);

// Set secure cookie parameters
ini_set('session.cookie_httponly', 1);
ini_set('session.cookie_secure', 1);

// Check if the user is logged in
if (isset($_SESSION['user_id'])) {
    // User is logged in
    echo "Welcome, " . $_SESSION['username'];
} else {
    // User is not logged in
    header("Location: login.php");
    exit;
}

// ... rest of the code
```

### &#10022; Strong Session Name:
This is a unique identifier for session variables that makes it harder for attackers to guess or brute-force the session ID. This is a crucial and important security measure in session handling to protect user sessions.

*Example:*
```php
session_name('my_secure_session_name');
// strong unpredictable random name that used to create session in the name mentioned
session_start();
```

### &#10022; Session Handlers:
It is a mechanism that allows to customize session data handling. By default, PHP uses files to store session data on the server, but it can be customized to use databases, memcached, or other storage systems.

- Need for session handler:
	- Scalability: For high-traffic websites, database-based sessions can offer better performance and scalability.
 	- Security: Custom handlers can be robust security measures, such as encryption and token-based authentication.
	- Flexibility: It gives possibilities to tailor the session handling to the specific needs, such as implementing custom session expiration policies or data retention strategies.

### &#10022; Example For Custom Session Handlers:

- Define the Handler Functions: Define following functions to handle session operations,
   - `session_open()`
   - `session_close()`
   - `session_read()`
   - `session_write()`
   - `session_destroy()`
   - `session_gc()`

- Register the Handler: using the function `session_set_save_handler()`.

*Example: Database-Based Session Handler*

```php
function session_open() {
		try {
	    // Connect to the database
	    $dsn = "mysql:host=" . $dbhost . ";dbname=" . $dbname;            
	    $db =  new PDO($dsn, $dbusername, $dbpassword);
	    $db->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION); 
		} catch (PDOException $e) {
			print "Error " . $e->getMessage() . PHP_EOL;
      die(); 
    }

    return true;
}

function session_close() {
    $GLOBALS['db']->close();
    return true;
}

function session_read($id) {
    $query = "SELECT session_data FROM sessions WHERE session_id = :session_id";
    $stmt = $GLOBALS['db']->prepare($query);
    $stmt->execute(array(':session_id' => $id));
    if ($GLOBALS['db']->rowCount() > 0) {
    		$row = $GLOBALS['db']->fetchAll();        
        return $row['session_data'];
    }
    return '';
}

function session_write($id, $data) {
    $query = "INSERT INTO sessions (session_id, session_data) VALUES (:session_id, :session_data_old) ON DUPLICATE KEY UPDATE session_data = :session_data";
    $stmt = $GLOBALS['db']->prepare($query);
    $stmt->execute(array(':session_id' => $id, ':session_data_old' => $data, ':session_data' => $data));
    return true;
}

function session_destroy($id) {
    $query = "DELETE FROM sessions WHERE session_id = :session_id";
    $stmt = $GLOBALS['db']->prepare($query);
    $stmt->execute(array(':session_id' => $id));
    return true;
}

function session_gc($maxlifetime) {
    $query = "DELETE FROM sessions WHERE session_time < :session_time";
    $time = time() - $maxlifetime;
    $stmt = $GLOBALS['db']->prepare($query);
    $stmt->execute(array(':session_time' => $time));
    return true;
}

// Register the custom session handler
session_set_save_handler(
    "session_open",
    "session_close",
    "session_read",
    "session_write",
    "session_destroy",
    "session_gc"
);

// Start the session
session_start();
```

*Example: Class based session handler* 
Create a class that implements the `SessionHandlerInterface`. This interface defines required methods for a session handler:
 ```php
class CustomSessionHandler implements SessionHandlerInterface {
   public function open($save_path, $session_name) {
       // Connect to the storage system (e.g., database, file)
       // ...
       return true;
   }

   public function close() {
       // Close the connection to the storage system
       // ...
       return true;
   }

   public function read($session_id) {
       // Retrieve session data from the storage system
       // ...
       return $data;
   }

   public function write($session_id, $session_data) {
       // Store session data in the storage system
       // ...
       return true;
   }

   public function destroy($session_id) {
       // Delete session data from the storage system
       // ...
       return true;
   }

   public function gc($maxlifetime) {
       // Clean up expired sessions
       // ...
       return true;
   }
}
 
// Register the Handler:
session_set_save_handler(new CustomSessionHandler());
session_start();
```
*Example: Class based session handler with database based storage system.* 

```php
class DatabaseSessionHandler implements SessionHandlerInterface {
    private $pdo;

    public function __construct($dsn, $username, $password) {
        $this->pdo = new PDO($dsn, $username, $password);
    }

    // Implement the remaining and required methods (open, close, read, write, destroy, gc)
    // using PDO to interact with the database. For example:

    public function read($session_id) {
        $stmt = $this->pdo->prepare('SELECT data FROM sessions WHERE session_id = ?');
        $stmt->execute([$session_id]);
        $row = $stmt->fetch(PDO::FETCH_ASSOC);
        return $row['data'] ?? '';
    }

    // ... other methods ...
}

// Register the database session handler
$dsn = 'mysql:host=localhost;dbname=my_database';
$handler = new DatabaseSessionHandler($dsn, $username, $password);
session_set_save_handler($handler);
session_start();
```

### &#10022; Protecting Against Session Fixation:
It is a type of attack where an attacker tricks a user with a specific session ID, allowing them to hijack the user session.

*Some techniques to mitigate the risk:*
- Session Regeneration:
	Regularly regenerate the session ID: This makes harder to predict and exploit the session ID. Implement it after user authentication to further strengthen security.
	
*Example:*
```php
session_start();
// Regenerate session ID after login
if ($logged_in) {
    session_regenerate_id(true);
}
```

- Secure Cookie Settings:
	`HttpOnly` Flag prevents client-side scripts from accessing the session cookie, prevents attackers to steal or manipulate it. `Secure` Flag ensures that the cookie is only sent over HTTPS connections.

*Example:*
```php
ini_set('session.cookie_httponly', 1);
ini_set('session.cookie_secure', 1);
```

- Strong Session IDs:
	Use a strong random alpha numeric generator for generate custom session IDs. To avoid predictable patterns in session IDs.

---
[&#8682; To Top](#-sessions)

[&#10094; Previous Topic](./forms-and-data-handling.md) &emsp; [Next Topic &#10095;](./cookies.md)

[&#8962; Goto Home Page](../README.md)