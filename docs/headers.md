## &#10162; Headers:
Headers are pieces of information sent from the server to the client browser before the actual content. It control and decides how the browser to react and displays the content.

### &#9780; Overview:
1. [Setting a Header](#-setting-a-header)
2. [Common Headers](#-common-headers)
3. [Content Type](#-content-type)
4. [Redirection](#-redirection)
5. [Cache Control](#-cache-control)
6. [Order of Usage](#-order-of-usage)
7. [Headers with Output Buffers](#-headers-with-output-buffers)
8. [Security Headers](#-security-headers)

### &#10022; Setting a Header:
PHP provides the `header()` function to send headers. It is important to set and sent headers before any output is sent to the browser.

### &#10022; Common Headers:
PHP provides common and different usages of header:
- Content-Type: Specifies the MIME type of the content is sent.
  ```php
  header('Content-Type: text/html');
  ```
- Location: Redirects the user browser to a specified URL. and Important to add exit statement at end of the header for redirect to avoid continuous execution of the script. 
  ```php
  // redirect to page1 
  header('Location: page1.php');
  exit;
  // redirect to external site
  header('Location: https://www.example-host.com');
  exit;
  ```
- Set-Cookie: Sets a cookie.
  ```php
  header('Set-Cookie: name=value; expires=Wed, 01 Jan 2025 00:00:00 GMT; path=/');
  ```
- Cache-Control: Controls browser caching.
  ```php
  header('Cache-Control: no-cache, no-store, must-revalidate');
  ```
- Expires: Sets an expiration date for the content.
  ```php
  header('Expires: Wed, 01 Jan 2025 00:00:00 GMT');
  ```

*Example:*
```php
header('Content-Type: text/html');
header('Cache-Control: no-cache, no-store, must-revalidate');

echo '<h1>Welcome, User!</h1>';
```

- Important Considerations:
	- `Header Sending Order`: Headers must be set and sent before any output is sent to the user browser. Because, it throws an error that headers are already sent.
	- `Output Buffering`: Send headers correctly when using `ob_start()` and `ob_end_flush()`.
	- `HTTP Status Codes`: Send appropriate HTTP status codes to indicate the status of the request.
	- `Security Headers`: Implement required security headers such as `X-Frame-Options`, `X-XSS-Protection`, and `Content-Security-Policy` to prevent and protect application from attacks.

### &#10022; Content Type:
This headers are used to specify the MIME media type of the resource being sent to the user browser. This information allows the browser to control and interpret to display the content correctly.

- Text-based Content:
	- Plain Text:
   ```php
   header('Content-Type: text/plain');
   ```
	- HTML:
   ```php
   header('Content-Type: text/html');
   ```
	- CSS:
   ```php
   header('Content-Type: text/css');
   ```
	- JavaScript:
   ```php
   header('Content-Type: text/javascript');
   ```

- Application-based Content:
	- JSON:
   ```php
   header('Content-Type: application/json');
   ```
	- PDF:
   ```php
   header('Content-Type: application/pdf');
   ```
	- XML:
   ```php
   header('Content-Type: application/xml');
   ```

- Image-based Content:
	- JPEG:
   ```php
   header('Content-Type: image/jpeg');
   ```
	- PNG:
   ```php
   header('Content-Type: image/png');
   ```
	- GIF:
   ```php
   header('Content-Type: image/gif');
   ```

- Additional Considerations:
	- Character Encoding: To specify the character encoding using the `charset` parameter:
  ```php
  header('Content-Type: text/html; charset=utf-8');
  ```
	- File Download: To force the browser to download a content as file using the `Content-Disposition` header:
  ```php
  header('Content-Type: application/pdf');
  header('Content-Disposition: attachment; filename="document.pdf"');
  ```
  - Caching: Set `Cache-Control` and `Expires` headers to control browser caching.
  ```php
  header('Cache-Control: max-age=3600');
  header('Expires: ' . gmdate('D, d M Y H:i:s \G\M\T', time() + 3600));
  ```

### &#10022; Redirection:
To redirect user browser to a specified URL. This is achieved by setting the `Location` property in header. and It is important to set exit statement after header statement.

- Basic Redirection:
```php
header("Location: page2.php"); // it redirect via relative URL
exit;
header("Location: https:// ". $_SERVER["HTTP_HOST"] ."/page2.php"); // it redirect via absolute URL
exit;
header('Location: https://www.example-host.com'); // redirect to external URL
exit;
```

- Temporary and Permanent Redirects:
To specify the type of redirect using different status codes:
	- Temporary redirect can be possible by set and send `302 Found` status code. The original URL is still accessible.
	- Permanent redirect can be possible by set and send `301 Moved Permanently` status code. The original URL is no longer accessible.

```php
// Temporary redirect
header('Location: https://www.example-host.com', true, 302);

// Permanent redirect
header('Location: https://www.example-host.com', true, 301);
```

- Redirecting Based on Conditions:

```php
if ($userIsLoggedIn) {
    header('Location: dashboard.php');
} else {
    header('Location: login.php');
}
```

- Redirecting After Form Submission:

```php
if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    // Process form data
    header('Location: success.php');
    exit;
}
```

- Best Practices for Redirects:
	- `Exit Statement`: Important to add `exit` statement, When using redirect Location type in header.
	- `Status Code`: Send the correct status code based on the nature of the redirect. When redirect it sends 302 status code to the browser by default, but use redirect with 303 status code that has cacheable never and always prefers `get` request method. Which is used to avoid double entry problem with resubmission of form.
	- `Avoid unnecessary redirects`: Too many redirects that can affects the application performance.
	- `Test redirects`: Ensure that redirects that works as expected to point correctly in different browsers and environments.
	- `Consider user experience`: Provide clear informative messages before and during redirects.
	- `Security`: Be cautious with redirects to avoid security vulnerabilities like open redirects.

### &#10022; Cache Control:
These are HTTP headers that control cache resources on the browsers. It is crucial for optimizing website performance and reducing server load.

- Common Cache Control Headers:
	- *Cache-Control:*
	   	- max-age: It specifies the expiry of a resource in seconds.
	   	- s-maxage: It specifies the expiry of a resource for shared caches.
	   	- public: It allows any cache to store the resource.
	   	- private: It allows only the user browser to cache the resource.
	   	- no-cache: It prevents caching of the resource.
	   	- no-store: It prevents the resource to stored on any cache.
	   	- must-revalidate: The cache should validate the resource with the origin server before use it.
		
	- *Expires:* It sets content expiry, It specifies an absolute expiration date for the resource.
	- *Last-Modified:* It sets content modified, It specifies the last modification date of the resource.

```php
header('Cache-Control: public, max-age=3600'); // Cache for 1 hour
header('Expires: ' . gmdate('D, d M Y H:i:s \G\M\T', time() + 3600));
```

### &#10022; Order of Usage:
Once PHP sends output to the browser, it cannot possible to send headers. This lead to unexpected behavior and errors. It may able to send multiple headers to the browsers. 

- General Order:
	- `Status Code Header`: Sets the HTTP status code, such as 200 OK, 404 Not Found, or 302 Found.
	- `General Headers`: Provide general information about the resource, such as `Date`, `Server`, and `Connection`. Example: `header('Date: ' . gmdate('D, d M Y H:i:s \G\M\T'));`
	- `Request Headers`: Provide information about the request, such as `Accept`, `User-Agent`, and `Referer`. These are usually sent by the client, not the server.
	- `Response Headers`: Provide information about the response, such as `Content-Type`, `Content-Length`, `Cache-Control`, and `Expires`.
	- `Cookie Headers`: Set cookies for the browser.

- Common Mistakes:
	- `Accidental Output`: Even a single space or newline space before the `header()` function can lead error and prevent it from working.
	- `Including Files`: Including files with output content before the header send can cause error.
	- `Incorrect use of output buffers`: If it is not used correctly, output buffering can interfere with header.

- Best Practices:
	- `Send Headers Early`: Send headers as soon as possible in the script, before any output is generated.	   
	- `Check for Output`: Use the `headers_sent()` function to check if any output has been sent.
	- `Header Order`: Use multiple headers in the proper order.

*Example:*
```php
// Send headers before any output send
header('Content-Type: text/html');
header('Cache-Control: no-cache');

// output content
echo 'Welcome, user!';
```

### &#10022; Headers with Output Buffers:
It is important to use header correctly in output buffers.

- Start Output Buffering:
   ```php
   ob_start();
   ```
- Send Headers:
   ```php
   header('Content-Type: text/html');
   header('Cache-Control: no-store, no-cache, must-revalidate, max-age=0');
   ```
- Generate Content:
   ```php
   echo '<h1>Welcome, user!</h1>';
   ```
- Flush Output Buffer:
   ```php
   ob_end_flush();
   ```

*Example:*
```php
ob_start();

// Set headers
header('HTTP/1.1 200 OK');
header('Content-Type: text/html');

// Generate HTML content
include 'page1.php'

ob_end_flush();
```

### &#10022; Security Headers:
It sent to a browser to enhance the security of a web application. By setting these headers, To mitigate various security vulnerabilities, such as cross-site scripting (XSS), clickjacking, and others.

- Common Security Headers:
	-	Content-Security-Policy (CSP): It restricts a browser to load the resources and It helps to prevent XSS attacks.
   ```php
   header('Content-Security-Policy: default-src \'self\'; script-src \'self\'');
   ```
	- X-Frame-Options: It controls a page to load in an iframe or not and It helps to prevent clickjacking attacks.
   ```php
   header('X-Frame-Options: DENY'); // Disallow iframes
   // or
   header('X-Frame-Options: SAMEORIGIN'); // Allow iframes from the same origin
   ```
	- X-XSS-Protection: It controls the browser to enable built-in XSS protection mechanisms.
   ```php
   header('X-XSS-Protection: 1; mode=block');
   ```
	- Strict-Transport-Security (HSTS): It forces the browsers to only connect to the website using HTTPS.
   ```php
   header('Strict-Transport-Security: max-age=31536000; includeSubDomains');
   ```
	- Referrer-Policy: It controls how much referrer information to sent with requests.
   ```php
   header('Referrer-Policy: no-referrer'); // Don't send any referrer information
   ```

---
[&#8682; To Top](#-headers)

[&#10094; Previous Topic](./forms-and-data-handling.md) &emsp; [Next Topic &#10095;](./http-status-code.md)

[&#8962; Goto Home Page](../README.md)