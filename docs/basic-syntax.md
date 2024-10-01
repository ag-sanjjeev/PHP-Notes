## &#10162; Basic Syntax:
PHP has certain syntax and structure to create a valid script that executes on web server. 

### &#9780; Overview:
1. [Variables](#-variables)
2. [Data Types](#-data-types)
3. [Operators](#-operators)

### &#10022; Variables:
It is used to store data that can be handled throughout the program. To declare a variable in PHP using a `$` symbol followed by a name. The variable name should follow certain rules:
  - It can start with a letter or underscore (_).
  - It can contain letters, numbers, and followed by underscores.
  - Variable names are case-sensitive (e.g., `$age` is different from `$Age`).
  - It cannot be a reserved keyword in PHP.

```php
$name = '';
$age = ''
$is_loggedin = false;
$value1 = 0;
$value_2 = 0;
```

### &#10022; Data Types:
PHP defines the kind of information that a variable can hold. That data types does not required to explicitly declare in most cases. PHP automatically takes the data type based on the value assigned to the variable. PHP has several built-in data types: 
- **Integer:** Whole numbers (e.g., 10, -5).
- **Float:** Decimal numbers (e.g., 3.14, -2.5).
- **String:** Sequence of characters that enclosed with quotes (single '' or double "").
- **Boolean:** Represents TRUE or FALSE state.
- **Array:** Series collection of items of any data type.
- **Object:** Represents a complex data structure with associated properties and methods.

```php
$name = "User name";    // String variable
$age = 30;              // Integer variable
$pi = 3.14159;          // Float variable
$is_loggedin = true;    // Boolean variable (TRUE)
```

### &#10022; Operators:
It can perform operations on variables and values. Common operators in PHP:
- **Arithmetic Operators:** can perform calculations like,
	- `+`: Addition
	- `-`: Subtraction
	- `*`: Multiplication
	- `/`: Division
	- `%`: Modulus (remainder after division)

- **Comparison Operators:** can compare between two values using operators like,
	- `==`: Equal to
	- `!=`: Not equal to
	- `<`: Less than
	- `>`: Greater than
	- `<=`: Less than or equal to
	- `>=`: Greater than or equal to

- **Logical Operators:** can combine conditions using operators like,
	- `&&`: AND (both conditions must be true)
	- `||`: OR (at least one condition must be true)
	- `!`: NOT (inverts the truth value)

```php
$a = 5;
$b = 6;

echo $a + $b;      // Output: 11 (addition)
echo $a > $b;      // Output: false (greater than)
echo $a && $b;     // Output: true (both conditions true)
```

---
[&#8682; To Top](#-basic-syntax)

[&#10094; Previous Topic](../introduction.md) &emsp; [Next Topic &#10095;](./control-flow.md)

[&#8962; Goto Home Page](../README.md)