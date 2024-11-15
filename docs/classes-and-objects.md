## &#10162; Classes and Objects:
`Class`: It is a blueprint or template, which holds the properties and methods that objects of that class will have.
`Object`: It is an instance of a class. It represents a specific entity with own state of properties and behavior of methods.

### &#9780; Overview:
1. [Defining Classes](#-defining-classes)
2. [Properties and Methods](#-properties-and-methods)
3. [Creating Objects](#-creating-objects)
4. [Object Destruction](#-object-destruction)
5. [Key Points](#-key-points)

### &#10022; Defining Classes:
Defining a class with keyword of `class` and followed by `ClassName`.

*Example:*
```php
class Person {
    public $name;

    public function __construct($name) {
        $this->name = $name;
    }

    public function greet() {
        echo "Welcome, $this->name.";
    }
}
```

### &#10022; Properties and Methods:
- `Properties`: These are variables that store the state of an object.
- `Methods`: These are functions that has behavior for an object.

### &#10022; Creating Objects:
Creating an object for a class is called Object Instantiation, Use `new` keyword followed by the `ClassName`:

```php
$person1 = new Person("Kumar");
```

### &#10022; Object Destruction:
PHP automatically destroys objects when no longer needed. However, to perform cleanup tasks or tasks that need to perform at the end of the object life cycle or before an object is destroyed, By define a destructor `__destruct()` method. 

```php
class Person {
    // ...

    public function __destruct() {
        echo "Object destroyed.";
    }
}
```

### &#10022; Key Points:
- Access Modifiers: `public`, `private`, and `protected` control the visibility of object properties and methods.
- Constructor: The `__construct()` method is automatically called when an object is created.
- Destructor: The `__destruct()` method is automatically called when before an object is destroyed.
- Object-Oriented Programming (OOP) Principles: [Encapsulation](./encapsulation.md), [inheritance](./inheritance.md), and [polymorphism](./polymorphism.md) are fundamental OOP concepts that is important in PHP application development.


---
[&#8682; To Top](#-classes-and-objects)

[&#10094; Previous Topic](./error-handling-and-debugging.md) &emsp; [Next Topic &#10095;](./inheritance.md)

[&#8962; Goto Home Page](../README.md)