## &#10162; Encapsulation:
Encapsulation is a fundamental principle in object-oriented programming that involves bundling properties and methods of a class. This helps in protecting and securing the state of an object and controlling access to properties and methods.

### &#9780; Overview:
1. [Access Modifiers](#-access-modifiers)
	- [Public](#-public)
	- [Protected](#-protected)
	- [Private](#-private)

### &#10022; Access Modifiers:
PHP provides three access modifiers to control the visibility of class members:
- [Public](#-public)
- [Protected](#-protected)
- [Private](#-private)

### &#10022; Public:
   - Accessible from anywhere, both within and outside of the class.
   - Declared using `public` keyword before properties and methods.

### &#10022; Protected:
   - Accessible within the class and child or subclasses.
   - Declared using `protected` keyword before properties and methods.

### &#10022; Private:
   - Accessible within the class only.
   - Declared using `private` keyword before properties and methods.

*Example:*
```php
class Person {
    public $name;
    private $age;
    protected $address;

    public function __construct($name, $age, $address) {
        $this->name = $name;
        $this->age = $age;
        $this->address = $address;
    }

    public function getDetails() {
        return "Name: $this->name, Age: $this->age, Address: $this->address";
    }
}

class Employee extends Person {
    public function getEmployeeDetails() {
        return $this->getDetails();
    }
}

$person = new Person("Kumar", 25, "India");
echo $person->name; // Accessible
// echo $person->age; // Not accessible

$employee = new Employee("Velavan", 30, "India");
echo $student->getEmployeeDetails(); // Accesses public and protected properties
```

In above example:
- `$name` is defined as public, so it can be accessed from both inside and outside of class.
- `$age` is defined as private, so it can be accessed within the class only.
- `$address` is defined as protected, so it can be accessed within the class and child or subclasses.

---
[&#8682; To Top](#-encapsulation)

[&#10094; Previous Topic](./polymorphism.md) &emsp; [Next Topic &#10095;](./abstraction.md)

[&#8962; Goto Home Page](../README.md)