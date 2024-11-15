## &#10162; Polymorphism:
Polymorphism is a concept in object-oriented programming that allows objects of different types to be treated as if they were of the same type. In PHP, it is primarily achieved through method overriding and method overloading.

### &#9780; Overview:
1. [Method Overloading](#-method-overloading)
2. [Method Overriding](#-method-overriding)

### &#10022; Method Overloading:
Unfortunately, PHP does not directly support method overloading. But Method overloading involves defining multiple methods with the same name but different parameters.

However, This can be achieved similar behavior using techniques like default arguments, variable-length argument lists, or method overloading emulation with function overloading (same name for function as method).

*Example: Using Default Arguments*

```php
function greet($name = "User") {
    echo "Welcome, $name!";
}

greet(); // Output: Welcome, User!
greet("Kumar"); // Output: Welcome, Kumar!
```

*Example: Using Variable-Length Argument Lists*

```php
function sum(...$numbers) {
    $total = 0;
    foreach ($numbers as $number) {
        $total += $number;
    }
    return $total;
}

echo sum(1, 2, 3); // Output: 6
echo sum(1, 2, 3, 4); // Output: 10
```

### &#10022; Method Overriding:
It is possible by inheriting the parent class.

*Example:*
```php
class Shape {
    public function calculateArea() {
        echo "Calculating area";
    }
}

class Square extends Shape {
    public function calculateArea() {
        echo "Calculating area of square";
    }
}
```

---
[&#8682; To Top](#-polymorphism)

[&#10094; Previous Topic](./inheritance.md) &emsp; [Next Topic &#10095;](./encapsulation.md)

[&#8962; Goto Home Page](../README.md)