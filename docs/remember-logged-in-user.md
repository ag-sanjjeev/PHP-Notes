## &#10162; Remember Logged In User:
HTTP is stateless, that does not know about the user when visiting the page again. but session keeps track the user and maintains the state that how many times the user visit the page again.

When developing a web application with user authentication, It is important to identify the logged in user and remember that user even after sometimes. Remember user with [session](./sessions.md) and [cookie](./cookies.md) is easier. But if it is not handle with proper way then it lead to attacks such as session hijack and more. This example gives best practices and it may vary on implementations based on different scenario. Consult with experts before implement in practical.  

### &#9780; Overview:
1. [Best Practice](#-best-practice)
2. [Session Management](#-session-management)
3. [Generate Unique ID](#-generate-unique-id)
4. [Regenerate Unique ID](#-regenerate-unique-id)
5. [Set Unique ID](#-set-unique-id)
6. [Check for Unique ID](#-check-for-unique-id)
7. [Expiry Remember Token](#-expiry-remember-token)
8. [Remove Remember Token](#-remove-remember-token)

### &#10022; Best Practice:
The step are recommended to remember logged in user in a safe way:
	- Set a session name for the application or project. It should be unpredictable.
	- Start and Implement session management.
	- This creates a session id and it will set cookie in the browser.
	- Use that session id until the user before the login state change.	
	- After logged in, regenerate session id for the user. This will prevent session related attacks.
	- Use either session id or generate any other unique id as remember identity of the user.
	- Store that unique id in database as well as a cookie.
	- That unique id used to detect the valid logged in user with cookie.
	- Whenever changes in user logged state, regenerate that unique id and update on database as well as cookie.
	- After logged out, make that unique id invalid to use in future by remove in database and remove cookie.

*Allocate separate table in database for storing remember token if required.
Always prefer to use hashing and salting for passwords to store in database, that unreadable by others as well as machines.*

### &#10022; Session Management:
It is essential for track user and their activity across multiple pages on the domain.

When visiting a page, `session_start()` function will generate unique session id that stored as file in server. when response sent to the browser, that sets cookie in browser with same session id. 

`session_start()` function is defined before to of any content or before any content sent to the browser to avoid errors. So, HTTP headers sent first to the browser to set cookies and other things.

Once session started, That session can store session data as file on server. To storing a large data which take time to load and read that session data. It results in performance lag. Store small amount of data rather than large.

*Start the Session:*
```php
session_name('unpredictable_unique_session_name');	
session_start();
```

### &#10022; Generate Unique ID:
In practical, It is recommended minimum 128 bit key required or generate above 32 characters of length.

*Use session id as remember token:*
```php
session_start();
$unique_id = session_id();
```

*Custom unique id as Remember token:*
```php
session_start();
$unique_id = random_bytes(128);
$unique_id = bin2hex($unique_id);
```

*Set generated unique id in cookie:*
```php
// setting cookie
setcookie("remember_token", $unique_id, time() + 2592000); // Cookie expires in 30 days
```

### &#10022; Regenerate Unique ID:
`session_regenerate_id` function will regenerate session id by preserving data. Best practice is use to regenerate on each request, but it is written on server that cause performance issue. 

But preferable strategy is regenerate `unique id` whenever user state changes such as login, logged out, account registered, deactivated and so on.

### &#10022; Set Unique ID:
After successful authentication or any other user state changes, store necessary user information in cookie and session:

```php
// regenerate session id after user state changes
session_start();
session_regenerate_id();
$unique_id = session_id();
// update in database with new session id	
setcookie("remember_token", $unique_id, time() + 2592000); // Cookie expires in 30 days
```

### &#10022; Check for Unique ID:
On subsequent page loads and to remember user is logged in status by checking and validating that unique id from cookie and session:

```php
if (isset($_COOKIE['remember_token'])) {
	// User is remembered for logged in status
	// fetch details from database such as username
  echo "Welcome, " . $_SESSION['username'];
} else {
	// User is not logged in, redirect to login page
  header('Location: login.php');
  exit;
}
```

### &#10022; Expiry Remember Token:
After user is logged in, set remember token with expiry time in cookie.

To set session cookie `PHPSESSID` expiry time by using `ini_set()` function. But it is not recommend and not good practice to change PHP configuration and settings when using shared web hosting. 

The best practice is store the remember token in separate cookie using `setcookie()` function rather than setting on session. Store remember token in the database. And additionally, regenerate remember token and update on both side whenever user state changed. 

### &#10022; Remove Remember Token:
After logged out or account deactivation, remove remember token on both side. Destroy session data, Remove cookie and make unique id invalid or remove from database which ever is required. Remove that remember token on both client side cookie and server side session.

---
[&#8682; To Top](#-remember-logged-in-user)

[&#10094; Previous Topic](./php-mysql-integration.md) &emsp; [Next Topic &#10095;](./configuring-apache-server.md)

[&#8962; Goto Home Page](../README.md)