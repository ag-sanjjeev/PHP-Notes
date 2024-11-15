## &#10162; MVC Architecture:
MVC stands for Model View Controller. It is a design pattern that separates an application into three interconnected parts.

### &#9780; Overview:
1. [Understanding MVC Architecture](#-understanding-mvc-architecture)
2. [Building MVC](#-building-mvc)
3. [How it works](#-how-it-works)
4. [Advantages of MVC](#-advantages-of-mvc)

### &#10022; Understanding MVC Architecture:
- `Model`: It represents the data and business logic of the application. It interacts with the database and other data sources.
- `View`: It represents the presentation layer also known as the user interface.
- `Controller`: It is an intermediate control between the Model and View. It can handle user input,  processing form and data, and provides the appropriate view.

### &#10022; Building MVC:
- Model:
```php
class User {
    private $id;
    private $name;
    private $email;

    // ... getters and setters
}
```

- View:
```php
<html>
<head>
    <title>Home Page</title>
</head>
<body>
    <h1>Greeting from Admin:</h1>
    <p>Welcome <?php echo $user->getName(); ?></p>
</body>
</html>
```

- Controller:
```php
// Fetch user data using Model (from database)
$user = new User();
$user->setId($userid);

// Render the View
require 'home_page.php';
```

### &#10022; How it works:
- `User Request`: A user requests a home page.
- `Controller`: The controller receives the user request. It finds the appropriate method for the request and fetches the data using Model.
- `Model`: The model provides the respective data from database to the controller.
- `Controller`: The after processing the data. Controller shows the appropriate view with data.
- `View`: The View renders the HTML output as response with provided data back to the user.

### &#10022; Advantages of MVC:
- `Flexibility`: It is easier to customize the different parts of the application.
- `Reusability`: Models and views can be reused in the application.
- `Performance`: It can improve overall application performance due to separated logic.
- `Scalability`: MVC architecture can be used in large scale application which grows in complexity.
- `Security`: It provides security against common web application vulnerabilities.

---
[&#8682; To Top](#-mvc-architecture)

[&#10094; Previous Topic](./web-frameworks.md) &emsp; [Next Topic &#10095;](./security-best-practices.md)

[&#8962; Goto Home Page](../README.md)