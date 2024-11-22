## &#10162; Comments:
Comments are non-executable code in the script that can be added to PHP script to explain the code functionality and other useful information related to the script. Which improves readability and helpful in future for maintenance.

### &#9780; Overview:
1. [Single Line Comments](#-single-line-comments)
2. [Multi Line Comments](#-multi-line-comments)
3. [Doc Comments](#-doc-comments)
4. [Hash Comments](#-hash-comments)

### &#10022; Single Line Comments:
It is used to hold a single and one line comments.

*Syntax:`// Comment`*

```php
// This is a single-line comment
echo "Welcome, User!"; // This comment is followed by line of code after it.
```

### &#10022; Multi Line Comments:
It is used to hold multiple lines of comments.

*Syntax: `/* Comment */`*

```php
/*
This is a multi-line comment.
It may contain comments that span across continuous of multiple lines.
*/
echo "Welcome, User!";
```

### &#10022; Doc Comments:
It used to document code such as classes, methods, and functions. It can be used by tools like PHPdoc to generate documentation.

*Syntax:** `/** Comment */`*

```php
/**
 * This is a class to calculate the area of a square.
 */
class Square {
    /**
     * Calculates the area of the square.
     *
     * @param int $side of side of the square.
     * @return int The area of the square.
     */
    public function area($side) {
        return $side * $side;
    }
}
```

### &#10022; Hash Comments:
`#` (hash) is valid ways to create single-line comments in PHP. It depends on personal preference or coding style guidelines to choose it.

However, it is important that PHP 8 introduced, a new syntax for attributes using the hash symbol (`#`). So, while it can still use `#` for single-line comments, use with cautious in newer PHP versions to avoid conflicts with attributes. 

*Syntax: `# comment`*

```php
# This is a single-line comment using a hash symbol
$a = 6;
```

---
[&#8682; To Top](#-comments)

[&#10094; Previous Topic](./display-statements.md) &emsp; [Next Topic &#10095;](./control-flow.md)

[&#8962; Goto Home Page](../README.md)