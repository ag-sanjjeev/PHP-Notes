## &#10162; Design Patterns:
Design patterns provides reusable solutions to common software design problems. It provides blueprint for solving specific design challenges and promote code re-usability, maintainability, and scalability.

### &#9780; Overview:
1. [Common Patterns](#-common-patterns)
2. [Singleton Design Pattern](#-singleton-design-pattern)
3. [Factory Design Pattern](#-factory-design-pattern)
4. [Abstract Factory Design Pattern](#-abstract-factory-design-pattern)
5. [Adapter Design Pattern](#-adapter-design-pattern)
6. [Decorator Design Pattern](#-decorator-design-pattern)
7. [Facade Design Pattern](#-facade-design-pattern)
8. [Strategy Design Pattern](#-strategy-design-pattern)
9. [Command Design Pattern](#-command-design-pattern)
10. [Comparison among patterns](#-comparison-among-patterns)

### &#10022; Common Patterns:

**Creational Patterns:**
- [Singleton:](#-singleton-design-pattern) Ensures only one instance exist for a class.
- [Factory:](#-factory-design-pattern) Creates objects without specifying the exact class to be instantiated.
- [Abstract Factory:](#-abstract-factory-design-pattern) Creates families of related objects.

**Structural Patterns:**
- [Adapter:](#-adapter-design-pattern) Adapts an interface of a class to another interface.
- [Decorator:](#-decorator-design-pattern) Adds new behaviors to objects dynamically.
- [Facade:](#-facade-design-pattern) Provides a simplified interface to a complex system.

**Behavioral Patterns:**
- [Strategy:](#-strategy-design-pattern) Encapsulates different algorithms and allows them to be interchangeable.
- [Command:](#-command-design-pattern) Encapsulates a request as an object and parameterized different request.

### &#10022; Singleton Design Pattern:
This ensures a class has only one instance and provides a global point of access to it. This is useful for the classes that need access from different parts of an application, such as configuration classes, database connections, loggers and so on. It prevents potential issues and resource wastage.

*Example:* 
```php
class Application
{
    private static $instance;

    private final function __construct() {}

    public static function getInstance()
    {
        if (self::$instance === null) {
            self::$instance = new self();
        }
        return self::$instance;
    }

    public function log($message)
    {
        // Log the message
        echo "Logging: $message\n";
    }
}
```

*Usage:*
```php
$appInstance1 = Application::getInstance();
$appInstance2 = Application::getInstance();

// Both $logger1 and $logger2 refer to the same instance
$appInstance1->log('Message 1');
$appInstance2->log('Message 2');
```

*Explanation:*
- The constructor is private, preventing direct instantiation of the class.
- A static variable `$instance` is used to store that single instance.
- Static `getInstance()` method provides a global point of access to the instance. If the instance doesn't exist then it will create and stored in the `$instance` property. Subsequent calls to `getInstance()` method will return the same instance.

### &#10022; Factory Design Pattern:
This is a creational design pattern that provides a way to create objects without specifying their exact class. It minimizes and encapsulates the object creation process, making the code more easier to maintain, flexible and reusable.

*Example:*
```php
interface Shape {
    public function draw();
}

class Circle implements Shape {
    public function draw() 
    {
        echo "Drawing a circle";
    }
}

class Square implements Shape {
    public function draw() 
    {
        echo "Drawing a square";
    }
}

class ShapeFactory {
    public static function createShape($type) 
    {
        switch ($type) {
            case 'circle':
                return new Circle();
            case 'square':
                return new Square();
            default:
                throw new Exception("Invalid shape type");
        }
    }
}
```

*Usage:*
```php
$shape = ShapeFactory::createShape('circle');
$shape->draw(); // Output: Drawing a circle
```

*Explanation:*
- The interface defines a common blueprint method for all other classes who implements it.
- These concrete classes can implement the interface.
- Factory class provides a static method invokes a concrete class method based on the given type.
- These factory class to encapsulates without knowing the specific implementation.

*Benefits of the Factory Pattern:*
- The usage is simplified among multiple concrete classes by decoupling from the concrete implementations.
- New concrete class can be added without modifying the client code.
- The factory can be mocked for testing purposes.
- The factory encapsulates the object creation process, which makes the code more readable and maintainable.

### &#10022; Abstract Factory Design Pattern:
This is a creational design pattern and similar to Factory design pattern. Instead of specifying type, Following a common implementation pattern. It provides an interface for creating families of related objects without specifying their concrete classes. It is useful for create different sets of objects based on a specific need.

*Example:*
```php
// Factory Interface
interface GUIFactory {
    public function createButton();
    public function createTextField();
}

// Factory Class
class WindowsFactory implements GUIFactory {
    public function createButton() 
    {
        return new WindowsButton(); // concrete class
    }

    public function createTextField() 
    {
        return new WindowsTextField(); // concrete class
    }
}

// Factory Class
class MacFactory implements GUIFactory {
    public function createButton() 
    {
        return new MacButton(); // concrete class
    }

    public function createTextField() 
    {
        return new MacTextField(); // concrete class
    }
}
```

*Usage:*
```php
$factory = new WindowsFactory();
$button = $factory->createButton();
$textField = $factory->createTextField();
$button->render();
$textField->render();
```

*Explanation:*
- Factory Interface defines blueprint methods for the need or process.
- Concrete Factories or Factory Classes implement Factory interface and create a families of related objects.
- For specific need or process, specific factory class can be used.

*Benefits of the Abstract Factory Pattern:*
- This can be work across different needs and requirements as per implementations without modification.
- These factory classes can be reused in different parts of the application.
- The factory classes can be mocked for testing purposes.
- This will ensures a consistent and similar look and feel across through out the application.

### &#10022; Adapter Design Pattern:
This is a structural design pattern that allows incompatible interfaces to work together. This acts as a bridge between two different interfaces and making it compatible.

**Real-world Example:**

Consider legacy library system that uses a specific format for storing their data. To update the system by integrate this library system data with a modern approach that uses a different format. The Adapter pattern can help to bridge this gap.

*Implementation Example:*
```php
// Modern Interface
interface ModernDataFormat {
    public function getDataInModernFormat();
}

class LegacyDataFormat {
    public function getData() 
    {
        // Legacy approach to retrieve data
    }
}

// Adapter class
class LegacyDataAdapter implements ModernDataFormat {
    private $legacyData;

    public function __construct(LegacyData $legacyData) 
    {
        $this->legacyData = $legacyData;
    }

    public function getDataInModernFormat() 
    {
        $legacyData = $this->legacyData->getData();
        // Convert legacy data into modern format
        // ...
        return $modernData;
    }
}
```

*Usage:*
```php
$legacyData = new LegacyData();
$adapter = new LegacyDataAdapter($legacyData);
$modernData = $adapter->getDataInModernFormat();
```

*Explanation:*
- The legacy or existing class provides data in an old format.
- Modern interface defines the blueprint for modern data format.
- Adapter class adapts the legacy or existing data format as per the modern format. Which should have logic or process to convert the data in modern format by using a object as input.
- Using the adapter to interact with the legacy data in the modern format without affecting existing or legacy implementations.

*Benefits of the Adapter Pattern:*
- Reuses existing legacy system code without modifying it.
- Adapts legacy interfaces to new requirement.
- It isolates the adapter logic by making the code more modular and maintainable.

### &#10022; Decorator Design Pattern:
This is a structural design pattern, Which allows to add new behaviors to an existing objects dynamically. It is achieved by wrapping an object with another object that assign additional functionalities to it.

**Real-world Example:**

Consider an e-commerce application, that has checkout option after adding products to the cart. Then it will calculate net total price for the products by applying discount, tax, transport charges and so on. It can be possible by feature chaining using Decorator design pattern.

```php
class Cart {
	public function checkout($price)
	{
		return $price;
	}
}
```

Additional feature implementations:

```php

interface CartInterface {
    public function checkout($price);
}

class Cart implements CartInterface {
    public function checkout($price)
    {
        return $price;
    }
}

class Discount implements CartInterface {
    private $cart;

    public function __construct(CartInterface $cart)
    {
        $this->cart = $cart;
    }

    public function checkout($price)
    {
        $price = $this->cart->checkout($price);
        $discount = ($price > 1000) ? 5 : 0; // in percentage
        echo "Discount % ($discount) <br>";
        $discount *= $price / 100;
        echo "Discount $discount for the price of $price<br>";
        $price -= $discount;
        echo "Amount after discount $price <br>";
        return $price;
    }
}

class DeliveryCharges implements CartInterface
{
    private $cart;
    
    public function __construct(CartInterface $cart)
    {
        $this->cart = $cart;
    }

    public function checkout($price)
    {
        $price = $this->cart->checkout($price);       
        $deliveryCharges ??= 150;        
        echo ($price < 1000) ? "Delivery charges $deliveryCharges <br>" : "Delivery charges <del>$deliveryCharges</del> <br>";        
        $deliveryCharges = ($price < 1000) ? $deliveryCharges : 0; // in numbers
        $price += $deliveryCharges;
        echo "Price after delivery charges $price";
        return $price;
    }
}
```

*Usage:*
```php
$cart = new Cart();
$grandTotal = new Discount($cart); // pass cart object
$netTotal = new DeliveryCharges($grandTotal); // pass grandTotal object
$netTotal->checkout(950);
```

*Explanation:*
- Interface defines a common interface for base class and decorators classes.
- Base class implements the interface and provides basic functionality.
- Decorators classes implement the interface and wrap a interface object. It add additional behavior to the wrapped object.
- By combining decorators, It add multiple features without modifying the base class or core class.

*Benefits of the Decorator Pattern:*
- *Flexibility:** Adding new behaviors dynamically without modifying existing classes.
- *Reusability:* Decorators can be reused to add different functionalities to different objects.
- *Modular Design:* Decorators promote a flexible and modular design.
- It is a powerful tool for extending functionality without modifying existing code. It is often used in real-world scenarios like adding new features or customizing the behavior of existing application. 

### &#10022; Facade Design Pattern:
This is a structural design pattern, Which provides a simplified interface to a complex system. It hides the complexity of underlying multiple subsystems and provides a simple handle to control all other subsystems.

**Real-world Example:**

Consider a hotel management application system. It might involve multiple subsystems for handling bookings, payments, room assignments, etc. The Facade design pattern can provide a simplified interface to handle this complex system.

*Example:*
```php
interface HotelBookingInterface {
    public function bookRoom($roomType, $checkInDate, $checkOutDate);
    public function cancelBooking($bookingId);
    public function getRoomAvailability($checkInDate, $checkOutDate);
}

class HotelBookingFacade implements HotelBookingInterface {
    private $bookingSystem;
    private $paymentSystem;
    private $roomAssignmentSystem;

    public function __construct(BookingSystem $bookingSystem, PaymentSystem $paymentSystem, RoomAssignmentSystem $roomAssignmentSystem) 
    {
        $this->bookingSystem = $bookingSystem;
        $this->paymentSystem = $paymentSystem;
        $this->roomAssignmentSystem = $roomAssignmentSystem;
    }

    public function bookRoom($roomType, $checkInDate, $checkOutDate) 
    {
        // complex booking logic involving multiple subsystems
    }

    public function cancelBooking($bookingId) 
    {
        // complex cancellation logic involving multiple subsystems
    }

    public function getRoomAvailability($checkInDate, $checkOutDate) 
    {
        // complex availability check logic involving multiple subsystems
    }
}
```

*Explanation:*
- Subsystem Classes represent the complex subsystems.
- Facade Class provides a simplified interface to handle and use these subsystems. It hides the complexity of these multiple subsystems and provides a single point of entry.
- The usage can interact with the application through the Facade Class without needing to know the details of the underlying subsystems.

*Benefits of the Facade Pattern:*
- It provides a simplified interface to the complex systems.
- It decouples and hides the underlying subsystems to usages client.
- It makes the code more modular, easy to maintain and easier to understand system.

### &#10022; Strategy Design Pattern:
This is a behavioral design pattern, Which defines a family of algorithms, encapsulates them and makes them interchangeable. This design pattern gives possibilities to vary algorithm independently based on the client or user usage.

**Real-world Example:**

Consider an e-commerce website with different shipping strategies such as standard shipping, express shipping, and overnight shipping. The strategy design pattern can be used to encapsulate these shipping strategies and allow the user to choose the desired shipping method.

*Example:*
```php
// Strategy Interface
interface ShippingStrategy {
    public function calculateShippingCost($weight, $distance);
}

// Concrete Strategy class
class StandardShipping implements ShippingStrategy {
    public function calculateShippingCost($weight, $distance) 
    {
        // Calculate shipping cost based on standard shipping rates
        return $weight * $distance * 0.1;
    }
}

// Concrete Strategy class
class ExpressShipping implements ShippingStrategy {
    public function calculateShippingCost($weight, $distance) 
    {
        // Calculate shipping cost based on express shipping rates
        return $weight * $distance * 0.5;
    }
}

// Concrete Strategy class
class OvernightShipping implements ShippingStrategy {
	public function calculateShippingCost($weight, $distance) 
	{
        // Calculate shipping cost based on overnight shipping rates
        return $weight * $distance * 0.75;
	}
}

// Context class
class Order {
    private $shippingStrategy;

    public function setShippingStrategy(ShippingStrategy $strategy) 
    {
        $this->shippingStrategy = $strategy;
    }

    public function calculateShippingCost($weight, $distance) 
    {
        return $this->shippingStrategy->calculateShippingCost($weight, $distance);
    }
}
```

*Usage:*
```php
$order = new Order();
$order->setShippingStrategy(new StandardShipping());
$standardShippingCost = $order->calculateShippingCost(20, 50);

$order->setShippingStrategy(new ExpressShipping());
$expressShippingCost = $order->calculateShippingCost(20, 50);

$order->setShippingStrategy(new OvernightShipping());
$overnightShippingCost = $order->calculateShippingCost(20, 50);

echo "Standard Shipping Cost : $standardShippingCost <br>";
echo "Express Shipping Cost : $expressShippingCost <br>";
echo "Overnight Shipping Cost : $overnightShippingCost <br>";
```

*Explanation:*
- Interface defines a common method for implementation.
- Other concrete classes implements that defined interface.
- Context class holds a reference to a object of strategy concrete class and delegates the strategy.
- The client or user can set the desired strategy on the context class object, Which allows flexible usage.

*Benefits of the Strategy Pattern:*
- It can easily add new strategies without modifying the existing class.
- The strategies can be reused in different contexts.
- It easily test different strategies independently.
- This pattern promotes a clean code.

### &#10022; Command Design Pattern:
This is a behavioral design pattern, Which encapsulates a request as an object, and parameterize  different requests.

**Real-world Example:**
Consider a simple text editor, that can perform various actions like cut, copy, and paste. Each of these actions can be represented as a command object.

**PHP Implementation:**

```php
interface Command {
    public function execute();
}

class CopyCommand implements Command {
    private $text;

    public function __construct($text) 
    {
        $this->text = $text;
    }

    public function execute() 
    {
        // ...
    }
}

class PasteCommand implements Command {
    private $text;

    public function __construct($text) 
    {
        $this->text = $text;
    }

    public function execute() 
    {
        // ...
    }
}

// invoker class
class TextEditor {
    public function executeCommand(Command $command) 
    {
        $command->execute();
    }
}
```

*Usage:*
```php
$textEditor = new TextEditor();
$textEditor->executeCommand(new CopyCommand($text));
$textEditor->executeCommand(new PasteCommand($text));
```

*Explanation:*
- The `Command` interface defines a common method for all commands class.
- The commands classes implement the interface and encapsulate specific actions.
- The invoker class taking a command object and executing it.

*Benefits of the Command Pattern:*
- Separates the request from execution.
- It allows to perform various commands.
- New commands can be added without modifying the existing invoker.
- Commands can be tested independently.

### &#10022; Comparison among patterns:
| Design Pattern | Description | Use Case | Key Characteristics |
|---|---|---|---|
| **Singleton** | Ensure a class only has one instance and provides a global point of access. | Logging, configuration settings, database connections. | Single instance, global access point. |
| **Factory** | Create objects without specifying the exact class to be instantiated. | Creating objects based on configuration or runtime conditions. | Encapsulates object creation, promotes loose coupling. |
| **Abstract Factory** | Create families of related objects. | Creating platform-specific UI components, database connections, etc. | Encapsulates object creation for families of objects. |
| **Adapter** | Adapt an interface of a class to another interface. | Integrating legacy systems with modern frameworks, adapting third-party libraries. | Adapts incompatible interfaces, promotes reusability. |
| **Decorator** | Add new behaviors to objects dynamically. | Adding features to objects at runtime, such as logging, caching, or security. | Extends functionality dynamically, promotes modularity. |
| **Facade** | Provide a simplified interface to a complex system. | Simplifying access to complex subsystems. | Hides complexity, provides a simpler interface. |
| **Strategy** | Encapsulate algorithms and allow that algorithms to be interchangeable. | Implementing different algorithms for the same task, such as sorting or searching. | Allows for flexible algorithms, promotes loose coupling. |
| **Command** | Encapsulate a request as an object and parameterize clients with different requests. | Undo/redo functionality, command queuing, macro recording. | Decouples the request from its execution, supports undo/redo. |



---
[&#8682; To Top](#-design-patterns)

[&#10094; Previous Topic](./performance-optimization.md) 

[&#8962; Goto Home Page](../README.md)