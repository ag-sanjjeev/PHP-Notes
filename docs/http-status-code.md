## &#10162; HTTP Status Code:
HTTP status codes are used to communicate the status of a web server response for the user request to the browser.

### &#9780; Overview:
1. [1xx Information](#-1xx-information)
2. [2xx Success](#-2xx-success)
3. [3xx Redirection](#-3xx-redirection)
4. [4xx Client Error](#-4xx-client-error)
5. [5xx Server Error](#-5xx-server-error)
6. [Usage](#-usage)

### &#10022; 1xx Information:
This series of status code used for information purpose.
	- 100 Continue: The client should continue with the request.
	- 101 Switching Protocols: The server is switching protocols.

### &#10022; 2xx Success:
This series of status code used for successful status for the request.
	- 200 OK: The request was successful.
	- 201 Created: The request was successful, and a new resource was created.
	- 202 Accepted: The request was accepted for processing, but the processing has not been completed.
	- 204 No Content: The request was successful, but there is no content.

### &#10022; 3xx Redirection:
This series of status code used for redirection purpose.
	- 301 Moved Permanently: The resource has been permanently moved to a new location.
	- 302 Found: The resource has been temporarily moved to a new location.
	- 304 Not Modified: The resource has not been modified since the last request.

### &#10022; 4xx Client Error:
This series of status code used for client side error.
	- 400 Bad Request: The request was invalid.
	- 401 Unauthorized: The request requires authentication.
	- 403 Forbidden: The server understood the request but refuses to fulfill it.
	- 404 Not Found: The requested resource could not be found.
	- 405 Method Not Allowed: The method specified in the request is not allowed for the resource.
	- 409 Conflict: The request could not be completed due to a conflict with the current state of the resource.

### &#10022; 5xx Server Error:
This series of status code used for server errors.
	- 500 Internal Server Error: A generic error that indicates the server encountered an error.
	- 503 Service Unavailable: The server is currently unavailable.

### &#10022; Usage:
To send HTTP status code using the `http_response_code` function with status code.

*Example:*
```php
http_response_code(404);
echo "Page not found";
```

---
[&#8682; To Top](#-http-status-code)

[&#10094; Previous Topic](./headers.md) &emsp; [Next Topic &#10095;](./sessions.md)

[&#8962; Goto Home Page](../README.md)