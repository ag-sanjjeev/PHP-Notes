## &#10162; Performance Optimization:
It is an important thing when comes into web application development. and it is noticeable issue for a large scale application. It is required to improve the speed of the process and optimizing the performance of overall application.

### &#9780; Overview:
1. [Caching Techniques](#-caching-techniques),
2. [Code Optimization](#-code-optimization)

### &#10022; Caching Techniques:
It is used to store frequently accessed data in memory or on disk to reduce the need for repeated process or calculations or database queries.

*The common caching techniques:*
- Output Caching:
   - It can caches the entire output of a script.
   - It is useful for both static content and pages that change infrequently.
   - PHP offers built-in caching mechanisms for output caching.

- Page Caching:
   - It can caches the rendered HTML output of a page.
   - It can be implemented using built-in caching mechanisms or libraries.

- Database Caching:
   - It caches database query results to reduce database load for repeated same queries.
   - It can be implemented by views in database or using third-party tools like Redis or Memcached.

- Other Caching:
	 - Use CDN (Content Delivery Network) can cache static assets to improve performance.
	 - Prefer Browser Caching, by using HTTP headers to instruct browsers to cache static assets like CSS, JavaScript, and images.

### &#10022; Code Optimization:
- Efficient Algorithms and Data Structures:
   - It is necessary to choose appropriate and optimistic algorithms and data structures.
   - Prefer to use built-in functions and libraries than custom algorithm for common task such as sort, search, etc.

- Minimize Database Load:
   - Prefer to use JOINs to reduce the number of queries.
   - Use caching mechanisms such as views or third-party tool to store frequently accessed data.
   - Optimize queries for better performance.

- Optimize Loops:
   - Avoid unnecessary iterations and long loops.
   - Prefer to use more efficient loop constructs when possible
   - Use `yield` whenever possible construct loop.

- Reduce HTTP Requests:
   - Try to combine multiple files into one to reduced HTTP requests.
   - Use CSS image sprites technique, where use CSS to use portion of image that has combination of all images.

- Minimize HTTP Redirects:
   - Try to reduce the number of redirects to improve page load time.

- Use Built-in Functions:
   - Use built-in functions for efficient array operations rather than using custom algorithm.

- Minify and Compress Assets:
   - Minify CSS, and JavaScript files to reduce file size to load quicker in the page.
   - Compress files, such as images to reduce transfer time.

---
[&#8682; To Top](#-performance-optimization)

[&#10094; Previous Topic](./cli-with-php.md) &emsp; [Next Topic &#10095;](./unit-testing.md)

[&#8962; Goto Home Page](../README.md)