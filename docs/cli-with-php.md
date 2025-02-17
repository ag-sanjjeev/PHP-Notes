## &#10162; CLI With PHP:
PHP offers to execute script through command line.

### &#9780; Overview:
1. [Executing PHP Script in Command Line](#-executing-php-script-in-command-line)
2. [Accepting Command Line Arguments](#-accepting-command-line-arguments)
3. [Common PHP CLI Options](#-common-php-cli-options)

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

### &#10022; Common PHP CLI Options:
- Basic Options:
	- `-a`: Interactive mode. Reads and executes code interactively.
	- `-c <path>`: Specifies the path to the php.ini file.
	- `-d <foo=bar>`: Defines an INI entry.
	- `-e`: Generates extended information for debuggers/profilers.
	- `-f <file>`: Specifies the file to execute.
	- `-h`: Displays help information.
	- `-i`: Prints information about the PHP configuration.
	- `-l`: Performs a syntax check only for the script.
	-	`-m`: Lists loaded modules.
	- `-n`: Disables the use of `php.ini`.
	- `-r <code>`: Executes a single line of PHP code.
	- `-s`: Outputs a syntax-highlighted source code.
	-	`-v`: Prints the PHP version.

- Additional Options:

	- `-B <begin_code>`: Executes code before processing input lines.
	- `-E <end_code>`: Executes code after processing all input lines.
	- `-F <file>`: Parses and executes a file for each input line.
	-	`-R <code>`: Executes code for every input line.
	-	`-S addr:port`: Runs a built-in web server for current directory.
	-	`-t <docroot>`: Specifies the document root for the built-in web server.

*Example:*

- Checking the PHP version:
  ```bash
  php -v
  ```
- Running PHP interactively:
  ```bash
  php -a
  ```
- Syntax checking a script:
  ```bash
  php -l my_script.php
  ```
- Checking PHP configuration:
  ```bash
  php -i
  ```
- Starting a built-in web server:
  ```bash
  php -S localhost:8000
  ```
- Running PHP code directly:
   ```bash
   php -r "echo 'Welcome';"
   ```

---
[&#8682; To Top](#-cli-with-php)

[&#10094; Previous Topic](./restful-api.md) &emsp; [Next Topic &#10095;](./performance-optimization.md)

[&#8962; Goto Home Page](../README.md)