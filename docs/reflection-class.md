## &#10162; Reflection Class:
Reflection class is a powerful feature in PHP that allows to inspect the structure of classes and their methods, properties at runtime. This can be useful for code generation, debugging and introspection.

### &#9780; Overview:
1. [Basic Usage](#-basic-usage)
2. [Key Features](#-key-features)
3. [Cautionary Note](#-cautionary-note)

### &#10022; Basic Usage:
```php
// Actual class definition
class ActualClass {
		// Class properties
    public $publicProperty = 'public';
    protected $protectedProperty = 'protected';
    private $privateProperty = 'private';

    // Class methods
    public function publicMethod() {
        echo 'Public method';
    }

    protected function protectedMethod() {
        echo 'Protected method';
    }

    private function privateMethod() {
        echo 'Private method';
    }
}

// Reflection class initiation
$reflectionClass = new ReflectionClass(ActualClass::class);

// Get actual class properties
foreach ($reflectionClass->getProperties() as $property) {
    echo $property->getName() . PHP_EOL;
}

// Get actual class methods
foreach ($reflectionClass->getMethods() as $method) {
    echo $method->getName() . PHP_EOL;
}
```

### &#10022; Key Features:
- Reflection classes used for code generation such as ORM Tools to generate SQL queries based on object and model class relationships.
- Testing frameworks might uses reflection to generate test cases automatically.
- Debugging tools might use reflection to inspect the state of objects at runtime.
- Reflection classes are use to log information about the current execution context such as the class name and their method name and properties.
- Reflection classes can be used to discover and load plugins dynamically.

### &#10022; Cautionary Note:
While reflection is a powerful tool, But it should be used judiciously. It is recommended to use reflection classes for specific tasks. It may reveal confidential data without proper usage.

---
[&#8682; To Top](#-reflection-class)

[&#10094; Previous Topic](./abstraction.md) &emsp; [Next Topic &#10095;](./namespace.md)

[&#8962; Goto Home Page](../README.md)