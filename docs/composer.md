## &#10162; Composer:
Composer is a tool for handling and managing dependencies in PHP. It allows to declare the libraries for the projects and manages by installing or updating that.

### &#9780; Overview:
1. [Dependency Management](#-dependency-management)
2. [Autoloading](#-autoloading)
3. [Handling Packages](#-handling-packages)
4. [Basic Usage](#-basic-usage)
5. [Composer Commands and Flags](#-composer-commands-and-flags)

### &#10022; Dependency Management:
It creates `composer.json` file for declaring dependencies for the project. Which require libraries with versions. It can download and install the specified dependencies automatically. It handles complex dependency relationships to ensure compatibility between different libraries.

### &#10022; Autoloading:
- Class Autoloading: Composer generates an autoloader that automatically loads classes as needed, reduces usage for manual `require` or `include` statements.

- PSR-4 Autoloading: Composer can support PSR-4 autoloading standards, which makes project structure and class loading more predictable.

### &#10022; Handling Packages:
- Package Discovery: Composer can discover packages from different sources including `Packagist` which is a public repository for PHP packages.

- Package Updates: Composer can easily update dependencies to their latest versions update command.
	
- Custom Packages: Composer can be used for creating custom packages of code and share it with others.

### &#10022; Basic Usage:
- Install Composer: To install composer, follow the instructions from [official site](https://getcomposer.org/) to install.
- Initiate Composer: Initiate project with composer by using `composer init` command.
- Add Libraries: After initiation, mention third party libraries in `composer.json` or by command.
- Download Libraries: After updating `composer.json`, run `composer install` command to download and install the required dependencies.

*Example:*
```json
{
	"require": {
		"php": "^8.1"
	}
}
```

*Example:* Add the composer autoload file in the PHP script to load dependencies.
```php
require 'vendor/autoload.php';
```

### &#10022; Composer Commands and Flags:
- Core Commands:
	- `init`: It create a new project and initialize Composer.
		```bash
		composer init
		```
	- `install`: It installs all dependencies listed in the `composer.json` file.
		```bash
		composer install
		```
	- `update`: It updates all dependencies to their latest compatible versions.
		```bash
		composer update
		```
	- `require`: Adds a new dependency to the `composer.json` file.
		```bash
		composer require monolog/monolog
		```
	- `remove`: Removes a dependency from the `composer.json` file and deletes it.
		```bash
		composer remove <package-name>
		```
	- `show`: Shows information about packages 
		```bash
		composer show
		```
	- `create-project`: Creates a new project based on a specified package template.
		```bash
		composer create-project laravel/laravel my-project
		```

- Additional Commands and Flags:
	- `self-update`: Updates Composer itself to the latest version available.		
	- `outdated`: Checks for outdated dependencies and packages.
	- `--dev`: It used with `require` command which adds and installs a development dependency.
	- `--no-dev`: It used with `require` command which adds and installs only production dependency.
	- `--no-interaction`: Skips interactive prompts for the commands.
	- `--prefer-dist`: Prefers installing packages from distributions.
	- `--prefer-source`: Prefers installing packages from source.
	- `--optimize-autoloader`: Optimizes the autoloader for better performance.
	- `--dry-run`: Simulates a command without making changes.

*Example:*

Optimizes the autoloader
```bash
composer dump-autoload -o
```

Checks for outdated packages
```bash
composer outdated
```

---
[&#8682; To Top](#-composer)

[&#10094; Previous Topic](./autoload-in-php.md) &emsp; [Next Topic &#10095;](./database-abstraction-layers.md)

[&#8962; Goto Home Page](../README.md)