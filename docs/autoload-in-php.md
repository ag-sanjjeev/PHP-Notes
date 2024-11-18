## &#10162; Autoload in PHP:
It is a mechanism that allows to load multiple other PHP scripts automatically.  It is difficult to use explicit declaration of `include` or `require` statements every time. It reduces the usages of explicit `include` or `require` statements. It is important for large scale applications to load multiple classes, interfaces and so on.

### &#9780; Overview:
1. [Built-in Autoloader](#-built-in-autoloader)
2. [How it works](#-how-it-works)

### &#10022; Built-in Autoloader:
PHP provides a built-in autoloader that can be used to load classes based on their namespace and file paths automatically.

```php
spl_autoload_register(function($classname) {
		$classname .= ".php";
		if (file_exists($classname)) {
    	require $classname;			
		}
});

// Now the class can be available without including the file
$obj = new MyNamespace\MyClass();
```

To autoload different namespace PHP scripts:
```php
spl_autoload_register(function($classname) {
    $classname = str_replace("\\", "/", $classname); 
    $classname .= ".php";
    if (file_exists($classname)) {
    	require $classname;
    }
});
// Now the class can be available without including the file
$obj = new MyClass();
```

To autoload different namespace on specific directory:
```php
spl_autoload_register(function ($class) {
    $file = __DIR__ . '/src/' . str_replace('\\', '/', $class) . '.php';
    if (file_exists($file)) {
        require_once $file;
    }
});
```

### &#10022; How it works:
1. When try to use a class, PHP checks for the class is already defined.
2. If the class is missing, then registered autoloader is triggered.
3. The autoloader searches for a file with specified name as the class in the specified directory.
4. If the file is found, it adds, making the class available.
5. If the class is not found throws an error.

---
[&#8682; To Top](#-autoload-in-php)

[&#10094; Previous Topic](./namespace.md) &emsp; [Next Topic &#10095;](./composer.md)

[&#8962; Goto Home Page](../README.md)