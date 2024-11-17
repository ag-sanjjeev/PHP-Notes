## &#10162; Include and Require Statements:
These statements are used to add the content of one PHP file into another. It is essential for organizing and reusing the code in larger projects.

### &#9780; Overview:
1. [Include Statement](#-include-statement)
2. [Require Statement](#-require-statement)
3. [Differences Between Statements](#-differences-between-statements)

### &#10022; Include Statement:
It can includes and executes the specified file in the PHP script. If the specified file is missing, a warning will be issued, but it would not interrupt execution of the script.

```php
include 'header.php'; // Include the header file
```

### &#10022; Require Statement:
It is similar to include statement, but it generates a fatal error, If the file is missing. It can be used to add essential files that are crucial and important for the script execution.

```php
require 'configuration.php'; // Require the configuration file
```

### &#10022; Differences Between Statements:
| Feature | include | require |
|---|---|---|
| Error Handling | Generates a warning that would not stop execution of the script | Generates a fatal error that interrupts the execution of script |
| File Inclusion | It adds the file at the point of the statement execution | It adds the file before execution of the script |
| Place of use | It can be used any where that file to be added | It is preferable to use at top level of the script |

---
[&#8682; To Top](#-include-and-require-statements)

[&#10094; Previous Topic](./file-handling.md) &emsp; [Next Topic &#10095;](./error-handling-and-debugging.md)

[&#8962; Goto Home Page](../README.md)