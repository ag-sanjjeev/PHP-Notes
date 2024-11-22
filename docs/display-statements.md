## &#10162; Display Statements:
PHP offers different ways to display output data to the browser.

### &#9780; Overview:
1. [Echo Statement](#-echo-statement)
2. [Print Statement](#-print-statement)
3. [Multi-line Printing](#-multi-line-printing)
4. [Printf Function](#-printf-function)
5. [Sprintf Function](#-sprintf-function)
6. [Print_r Function](#-print_r-function)
7. [Var_dump Function](#-var_dump-function)
8. [Vprintf Function](#-vprintf-function)
9. [Vsprintf Function](#-vsprintf-function)
10. [Comparison Among Statements](#-comparison-among-statements)

### &#10022; Echo Statement:
It is most common and one of the display and output statement in PHP. It efficient than any other display statements.

*Syntax:*
```php
echo expression1, expression2, ...;
```

*Explanation:*
- It prints one or more expressions.
- It doesn't return a value.
- It can be used without parentheses.

*Example:*
```php
echo "Welcome, user! ", "to the page";
echo "<p>This is a paragraph.</p>";
```

### &#10022; Print Statement:
It is most common and one of display and output statement in PHP. 

*Syntax:*
```php
print expression;
```

*Explanation:*
- It prints a single expression only.
- It returns 1 on success, 0 on failure.
- It requires parentheses sometimes.

*Example:*
```php
print("Welcome, user!");
print "<p>This is a paragraph.</p>";
```

### &#10022; Multi-line Printing:
To print multiple lines, use either `print` or `echo` with newlines:

*Example:*
```php
echo "Line 1\nLine 2\nLine 3";
```

*Example:* use `nl2br()` to convert newlines to `<br>` tags:
```php
echo nl2br("Line 1\nLine 2\nLine 3");
```

### &#10022; Printf Function:
The `printf()` function in PHP is used to format and print strings. It accepts a format string as the first argument and additional arguments as the subsequent parameters. The format string contains format specifiers that act as a placeholder that are replaced with the corresponding arguments.

*Syntax:*
```php
printf(format_string, argument1, argument2, ...);
```

*Explanation:*
- It formats output using placeholders in the format string.
- Format specifiers:

	| Specifier | Description | Example |
	|---|---|---|
	| %s | String | `printf("Name: %s", "Kumar")` |
	| %d | Integer | `printf("Age: %d", 30)` |
	| %f | Floating-point number | `printf("Pi: %.2f", 3.14159)` |
	| %e | Scientific notation | `printf("Avogadro's number: %e", 6.02214076e23)` |
	| %x | Hexadecimal number (lowercase) | `printf("Hexadecimal: %x", 255)` |
	| %X | Hexadecimal number (uppercase) | `printf("Hexadecimal: %X", 255)` |
	| %o | Octal number | `printf("Octal: %o", 255)` |
	| %b | Binary number | `printf("Binary: %b", 255)` |
	| %% | Literal percent sign | `printf("Percentage: %%")` |

- Additional Formatting Options:
	- Precision: Specify the number of decimal places for float numbers:
  ```php
  printf("Pi: %.3f", 3.14159); // Output: Pi: 3.142
  ```
	- Zero-padding: Use the `0` flag:
  ```php
  printf("Visits: %010d", 30); // Output: Visits: 000000030
  ```

*Example:*
```php
$name = "Kumar";
$age = 30;
printf("Name: %s, Age: %d\n", $name, $age);

$price = 36.89;
$hex = 0xFF;
$binary = 1010;

printf("Price: %.2f\nHex: %x\nBinary: %b\n", $price, $hex, $binary);
```

### &#10022; Sprintf Function:
It similar to `printf()` function, but returns the formatted string instead of printing it directly.

*Syntax:*
```php
$formatted_string = sprintf(format_string, argument1, argument2, ...);
```

*Example:*
```php
$name = "Kumar";
$age = 30;
$formatted_string = sprintf("Name: %s, Age: %d\n", $name, $age);
echo $formatted_string;
```

### &#10022; Print_r Function:
It prints human-readable information about a variable. For debugging and inspecting complex data structures.

*Syntax:*
```php
print_r(expression, boolean);
```

*Explanation:*
- It accepts optional second argument `boolean` to controls the output format:
  - `true`: Returns the output as a string.
  - `false` (default): Prints the output directly.

*Example:*
```php
$array = [1, 2, 3];
print_r($array);

echo print_r($array, true);
```

### &#10022; Var_dump Function:
It prints detailed information about one or more expressions, including their type and value. And it is useful for debugging.

*Syntax:*
```php
var_dump(expression1, expression2, ...);
```

*Example:*
```php
$array = [1, 2, 3];
var_dump($array);
```

### &#10022; Vprintf Function:
It is similar to `printf` function, but uses an array of arguments instead of number of variable arguments.

### &#10022; Vsprintf Function:
It is similar to `sprintf` function, but accepts array of arguments.

### &#10022; Comparison Among Statements:

| Function | Description | Return Value | Use Cases |
|---|---|---|---|
| `echo` | Outputs one or more strings | None | Simple output, printing HTML content |
| `print` | Outputs a single string | 1 on success, 0 on failure | Similar to `echo`, but can be used in one expression at a time |
| `printf` | Formats output using placeholders | None | Formatting output with specific data types (e.g., numbers, strings) |
| `sprintf` | Similar to `printf`, but returns the formatted string instead of printing it | Formatted string | Storing formatted strings for later use |
| `vprintf` | Like `printf`, but takes an array of arguments | None | Formatting output with number of arguments as a variable |
| `vsprintf` | Like `sprintf`, but takes an array of arguments and returns the formatted string | Formatted string | Storing formatted strings with a variable number of arguments |
| `print_r` | Prints human-readable information about a variable | None | Debugging and inspecting complex data structures (arrays, objects) |
| `var_dump` | Dumps information about a variable, including its type and value | None | Debugging and inspecting variables in detail |

**Choosing the Right Function:**
- Return Value: `print` returns 1 on success, while `echo` doesn't return anything.
- Argument Count: `echo` can take multiple arguments, while `print` takes only one.
- Formatting: `printf` and `sprintf` offer more control over formatting output using placeholders.
- Debugging: `print_r` and `var_dump` are useful for debugging and inspecting complex data structures.

---
[&#8682; To Top](#-display-statements)

[&#10094; Previous Topic](./basic-syntax.md) &emsp; [Next Topic &#10095;](./comments.md)

[&#8962; Goto Home Page](../README.md)