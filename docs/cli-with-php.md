## &#10162; CLI With PHP:
PHP offers to execute script through command line.

### &#9780; Overview:
1. [Executing PHP Script in Command Line](#-executing-php-script-in-command-line),
2. [Accepting Command Line Arguments](#-accepting-command-line-arguments)

### &#10022; Executing PHP Script in Command Line:
To execute PHP script in command line, use `php scriptname.php` in command line.

```bash
php test.php
```

### &#10022; Accepting Command Line Arguments:
To PHP accepts command line arguments and deliver through the variable `argv`.

```bash
php test.php arg1 arg2 arg3
```

```php
foreach ($argv as $arg) {
    echo $arg . "\n";
}
```

---
[&#8682; To Top](#-cli-with-php)

[&#10094; Previous Topic](./xml-and-json.md) &emsp; [Next Topic &#10095;](./debugging-and-profiling.md)

[&#8962; Goto Home Page](../README.md)