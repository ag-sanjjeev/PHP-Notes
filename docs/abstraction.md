## &#10162; Abstraction:
Abstraction is one of the fundamental concept in object-oriented programming that deals with an object by hiding unnecessary implementation details and by revealing essential features of it. In PHP, abstraction can be achieved using abstract classes, interfaces, and traits.

### &#9780; Overview:
1. [Abstract Classes](#-abstract-classes),
2. [Interfaces](#-interfaces),
3. [Traits](#-traits),
4. [Key Points](#-key-points),
5. [Real World Usages](#-real-world-usages)

### &#10022; Abstract Classes:
It is a class that cannot be instantiated directly. It serves as a blueprint for other classes. It contain both abstract and concrete methods.

- Abstract Methods:
	- It is declared without a body.
	- It must be implemented only by child classes.

- Usage:
  - It define common methods and properties for derived classes.
  - It enforce the implementation of specific methods in derived classes.

```php
abstract class Shape {
    abstract public function area();
    public function concreteMethod() {
        echo "Concrete methods";
    }
}

class Circle extends Shape {
    private $radius;

    public function __construct($radius) {
        $this->radius = $radius;
    }

    public function area() {
        return pi() * pow($this->radius, 2);
    }
}

$obj = new Circle(7);
echo $obj->area();
echo PHP_EOL;
echo $obj->concreteMethod();
```

### &#10022; Interfaces:
It is a contract that defines a set of methods that child or subclasses must implement. It can be used to enforce specific behaviors on classes.

- Usage:
  - It define a set of behaviors that can be implementable by other classes.
  - It makes loose coupling between classes.

```php
interface Shape {
    public function area();
}

class Circle implements Shape {
    private $radius;

    public function __construct($radius) {
        $this->radius = $radius;
    }

    public function area() {
        return pi() * pow($this->radius, 2);
    }
}

$obj = new Circle(6);
echo $obj->area();
```

### &#10022; Traits:
Traits are a mechanism for code reuse. That allows to include defined method in multiple classes.
- Usage:
  - To include traits in a class by `use` keyword.
  - To resolve conflicts between traits by `insteadof` keyword.

*Example: Simple trait*
```php
trait Logger {
    public function log($message) {
    		// ...
        echo "Logging: $message";
    }
}

class LoginController {
    use Logger;

    public function authenticate() {
        // ...
        $this->log("Logged in");
    }
}
```

*Example: Avoid conflict when using multiple traits*
```php
trait Logger {
    public function log($message) {
    		// ...
        echo "Logging: $message";
    }
}

trait DbLogger {
	public function log($message) {
		// ...
		echo "Logging: $message";
	}
}

class LoginController {
    use Logger, DbLogger {
    	DbLogger::log insteadof Logger;
    }

    public function authenticate() {
        // ...
        $this->log("Logged in");
    }
}

$obj = new LoginController();
$obj->authenticate();
```

### &#10022; Key Points:
- Abstract classes: It provides a base for inheritance and define common methods.
- Interfaces: It enforce specific behaviors on other classes.
- Traits: It allow to reuse code across multiple classes without inheritance.

### &#10022; Real World Usages:
- Abstract Class: 

*Example: Database Abstraction Layer*
```php
abstract class Database {
    protected $connection;

    abstract public function connect();
    abstract public function query($sql);
    abstract public function fetchAll();
}

class MySQLDatabase extends Database {
    // Implementation for MySQL
}

class PostgreSQLDatabase extends Database {
    // Implementation for PostgreSQL
}
```

- Interface: 

*Example: API Client Interface*
```php
interface ApiClient {
    public function sendRequest($url, $method, $data = []);
    public function parseResponse($response);
}

class RestApiClient implements ApiClient {
    // Implementations ...
}

class GraphQLClient implements ApiClient {
    // Implementations ...
}
```

*Example: Payment Gateway Interface*
```php
interface PaymentGateway {
    public function processPayment($amount, $cardDetails);
}

class StripePaymentGateway implements PaymentGateway {
    // Implementation with Stripe API
}

class PayPalPaymentGateway implements PaymentGateway {
    // Implementation with PayPal API
}
```

*Example: Cache Interface*
```php
interface CacheInterface {
    public function get($key);
    public function set($key, $value);
    public function delete($key);
}

class FileCache implements CacheInterface {
    // Implementation with file caching
}

class RedisCache implements CacheInterface {
    // Implementation with Redis
}
```

- Traits: 

*Example: Logging Trait*
```php
trait Logger {
    public function log($message) {
        // log method
        echo "Logging: $message\n";
    }
}

class LoginController {
    use Logger;

    public function authenticate() {
        // ...
        $this->log("Logged In");
    }
}
```

*Example: Validation Trait*
```php
trait ValidationTrait {
    public function validateEmail($email) {
        // validation logic for email addresses
    }

    public function validatePassword($password) {
        // validation logic for passwords
    }
}

class User {
    use ValidationTrait;

    public function register($email, $password) {
        $this->validateEmail($email);
        $this->validatePassword($password);
        // ...
    }
}
```

---
[&#8682; To Top](#-abstraction)

[&#10094; Previous Topic](./encapsulation.md) &emsp; [Next Topic &#10095;](./database-abstraction-layers.md)

[&#8962; Goto Home Page](../README.md)