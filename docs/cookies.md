## &#10162; Cookies:
It is a small text file stored on a users computer by a web server. It contains information about the user interaction and preferences with the website, such as login status, theme and shopping cart items.

### &#9780; Overview:
1. [Need and Usage](#-need-and-usage),
2. [Creating a cookie](#-creating-a-cookie),
3. [Modifying a cookie](#-modifying-a-cookie),
4. [Deleting a cookie](#-deleting-a-cookie),
5. [Pros](#-pros),
6. [Cons](#-cons)

### &#10022; Need and Usage:
- Authentication and authorization: Track user login status and sessions.
- Shopping Cart: Maintaining of items added to a shopping cart.
- Tracking User Behavior: Collect anonymous user data for analytics and personalization.
- User Preferences: Store user preferences like theme, language, or font size.

### &#10022; Creating a cookie:
To create a cookie in PHP, use `setcookie()` function:

*Parameters of `setcookie()`:*
- `name`: The name of the cookie.
- `value`: Sets value.
- `expire`: The expiration time of the cookie in seconds.
- `path`: Sets the path that cookie will available on the server.
- `domain`: Sets domain for that cookie is valid.
- `secure`: Whether the cookie should be transmitted over HTTPS only.
- `httponly`: Whether the cookie should be accessible through the HTTP protocol only.

```php
setcookie("username", "Kumar", time() + 43200); // Cookie expires in 12 hour
```

### &#10022; Accessing a cookie:
To access the value of a cookie using `$_COOKIE` [super global](./super-globals.md):

```php
echo $_COOKIE['username'];
```

### &#10022; Modifying a cookie:
To modify a cookie, by set a new value for it using `setcookie()` function.

```php
setcookie("username", "Kumaran", time() + 50000);
```

### &#10022; Deleting a cookie:
To delete a cookie, set the expiration time to the past date:

```php
setcookie("username", "", time() - 3600);
```

### &#10022; Pros:
- User Experience: It is used for personalize the user experience.
- Session Management: It is used for maintain user sessions.

### &#10022; Cons:
- Browser Limitations: Some browsers have limits on the number and size of cookies to be stored.
- Security Risks: Cookies can be vulnerable to attacks and modified on the user computers.
- User Privacy Concerns: Cookies are used to track users across multiple sites.

---
[&#8682; To Top](#-cookies)

[&#10094; Previous Topic](./sessions.md) &emsp; [Next Topic &#10095;](./file-handling.md)

[&#8962; Goto Home Page](../README.md)