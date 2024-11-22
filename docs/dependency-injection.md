## &#10162; Dependency Injection:
Dependency injection is a technique that promotes loose coupling between different components. It involves passing dependencies to a class constructor or methods via arguments.

### &#9780; Overview:
1. [Need for Dependency Injection](#-need-for-dependency-injection)
2. [Constructor Injection](#-constructor-injection)
3. [Setter Injection](#-setter-injection)
4. [Method Injection](#-method-injection)

### &#10022; Need for Dependency Injection:
- It allows easy testing by injecting mock or stub objects.
- It makes code more flexible and adaptable to changes.
- It allow to reuse components in different contexts with different needs.

### &#10022; Constructor Injection:
Dependencies are injected through the constructor arguments.

*Example:*
 ```php
Class Logger {
    public function log($message)
    {
        print $message;
    }
}

class ActualClass {
   private $logger;

   public function __construct(Logger $logger) {
       $this->logger = $logger;
   }

   public function execute() {
       $this->logger->log('executing');
   }
}

$logger = new Logger;
$obj = new ActualClass($logger);
$obj->execute();
 ```

### &#10022; Setter Injection:
Dependencies are injected through separate setter methods.

*Example:*
```php
Class Logger {
    public function log($message)
    {
        print $message;
    }
}

class ActualClass {
   private $logger;

    public function setLogger(Logger $logger) {
         $this->logger = $logger;
     }

   public function execute() {         
       $this->logger->log('executing');
   }
}


$logger = new Logger;
$obj = new ActualClass;
$obj->setLogger($logger);
$obj->execute();
```

### &#10022; Method Injection:
Dependencies are injected as arguments to methods.

*Example:*
```php
Class Logger {
    public function log($message)
    {
        print $message;
    }
}

class ActualClass {
   private $logger;

   public function execute(Logger $logger) {
       $this->logger = $logger;
       $this->logger->log('executing');
   }
}


$logger = new Logger;
$obj = new ActualClass;
$obj->execute($logger);
```

**Real-World Example:**
```php
class Product {
    public function __construct(public string $name, public float $price) {}
}

function calculateTotalPrice(array $products): float {
    $total = 0;
    foreach ($products as $product) {
        // validating whether it is a class object of Product Class
        if ($product instanceof Product) { 
            $total += $product->price;
        } else {
            // Handle invalid product
            throw new InvalidArgumentException('Invalid product class object');
        }
    }
    return $total;
}

// Usage:
$products = [
    new Product('Product 1', 10.35),
    new Product('Product 2', 50.75),
];
// Inject product class objects
$totalPrice = calculateTotalPrice($products);
echo $totalPrice;
```

---
[&#8682; To Top](#-dependency-injection)

[&#10094; Previous Topic](./reflection-class.md) &emsp; [Next Topic &#10095;](./namespace.md)

[&#8962; Goto Home Page](../README.md)