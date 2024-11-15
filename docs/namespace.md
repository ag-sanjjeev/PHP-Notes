## &#10162; Namespace:
A namespace is a declarative region that holds a set of definitions under specified namespace for classes, functions, constants, etc. It is used to prevent naming conflicts across multiple PHP scripts, Especially working with large scale projects or including external libraries.

### &#9780; Overview:
1. [Use of Namespace](#-use-of-namespace)
2. [Global Namespace](#-global-namespace)
3. [Declaration of Namespace](#-declaration-of-namespace)
4. [Implementation of Namespace](#-implementation-of-namespace)
5. [Namespace Alias](#-namespace-alias)
6. [Key Points](#-key-points)

### &#10022; Use of Namespace:
- Avoid Naming Conflicts: It prevents name clashes among identifiers with same name.
- Organize Code: It groups classes and functions into logical namespace.
- Improve Code Readability: It makes, the code organized and easier to understand.

### &#10022; Global Namespace:
If a class or function is not declared within a namespace, By default, it belongs to the global namespace. 

### &#10022; Declaration of Namespace:
Namespace for PHP script can be declared using the keyword `namespace`.

*Example:*
```php
namespace MyProject\MyNamespace;

class MyClass {
    // ...
}

function myFunction() {
    // ...
}
```

### &#10022; Implementation of Namespace:
If a class or function is declared within a namespace, It can not be accessed from global namespace. To use a class and function from a particular namespace, It can be implemented by either use the fully qualified name or import using the `use` keyword.

*Example:*
```php
// Fully qualified name:
\MyProject\MyNamespace\MyClass::myStaticMethod();

$obj = new \MyProject\MyNamespace\MyClass();
$obj->myMethod();
```

```php
// Using the `use` keyword:
use MyProject\MyNamespace\MyClass;

$obj = new MyClass();
$obj->myMethod();
```

### &#10022; Namespace Alias:
To shorten the fully qualified name of namespace, by create an aliases for namespace with the `as` keyword.

```php
use MyProject\MyNamespace as MPN;

$obj = new MPN\MyClass();
```

### &#10022; Key Points:
- Provide meaningful names for namespace declaration that reflect the project structure.
- Avoid too many nested namespace.
- Import namespaces with `use` keyword to improve code readability.
- Use a PSR-4 autoloader to automatically load classes based on their namespaces.


---
[&#8682; To Top](#-namespace)

[&#10094; Previous Topic](./abstraction.md) &emsp; [Next Topic &#10095;](./database-abstraction-layers.md)

[&#8962; Goto Home Page](../README.md)