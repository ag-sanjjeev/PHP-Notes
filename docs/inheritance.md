## &#10162; Inheritance:
Inheritance is a fundamental concept in object-oriented programming that allows to create new classes with properties and methods of existing classes. It promotes code reusability and helps to organize complex application systems.

### &#9780; Overview:
1. [Extending Classes](#-extending-classes)
2. [Overriding Methods](#-overriding-methods)
3. [Key Points](#-key-points)

### &#10022; Extending Classes:
To create a new class by inheriting from an existing class, with the use of `extends` keyword:
It can access only public and protected properties and methods of the parent class.

*Example:*
```php
// existing parent class
class ParentClass {
    public function parentMethod() {
        echo "Parent method";
    }
}

// Creating new class by inheriting the properties and methods
class ChildClass extends ParentClass {
    public function childMethod() {
        echo "Child method";
    }
}
```

### &#10022; Overriding Methods:
To override a extended method in a child class to provide a specific implementation:

*Example:*
```php
class Shape {
    public function draw() {
        echo "Drawing shape";
    }
}

class Circle extends Shape {
    public function draw() {
        echo "Drawing circle";
    }
}
```

### &#10022; Key Points:
- A child class can inherits all public and protected properties and methods from parent class.
- A child class can override extended methods of parent class.
- A child class can add own properties and methods.
- To access the parent class methods within the child class, Use `parent` keyword.

---
[&#8682; To Top](#-inheritance)

[&#10094; Previous Topic](./classes-and-objects.md) &emsp; [Next Topic &#10095;](./polymorphism.md)

[&#8962; Goto Home Page](../README.md)