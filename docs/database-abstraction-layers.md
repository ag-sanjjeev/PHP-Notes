## &#10162; Database Abstraction Layers:
PHP can integrate with different database and protect from various security attacks with database abstraction layers. It can provide approach to connect different databases with same method and perform database operations.

### &#9780; Overview:
1. [PDO](#-pdo),
2. [Prepared Statements](#-prepared-statements),
3. [Positional and Parameterized Queries](#-positional-and-parameterized-queries)

### &#10022; PDO:
PDO stands for PHP Data Objects, It provides a consistent interface for integrating different databases such as MySQL, PostgreSQL, SQLite, and others. 

Advantages:
- Consistent API: The same methods for interact with different database systems.
- Error Handling: It provides a standard error handling mechanism.
- Improved Performance: It optimizes query execution and reduces database load.
- Prepared Statements: It prevent SQL injection attacks.

*Connect to the Database:*
- PDO accepts DSN, user name and password to connect database.
- DSN stands for Data Source Name which holds database driver name, database host name and database name.

```php
// Database credentials
$dsn = 'mysql:host=localhost;dbname=test';
$username = 'user';
$password = 'password';

// Establishing database connection
try {
    $pdo = new PDO($dsn, $username, $password);
} catch (PDOException $e) {
    echo "Connection failed: " . $e->getMessage();
}
```

### &#10022; Prepared Statements:
It is a technique used to separate SQL statements from data. This technique prevents SQL injection. 

```php
$stmt = $pdo->prepare("SELECT * FROM users WHERE name = :name");
$stmt->bindValue(':name', 'Kumar');
$stmt->execute();

// Fetch all rows as an associative array
$result = $stmt->fetchAll(PDO::FETCH_ASSOC);

// Fetch the next row as an associative array
$row = $stmt->fetch(PDO::FETCH_ASSOC);
```

### &#10022; Positional and Parameterized Queries:
- Positional Queries:
This type of queries are prepared to bound `?` placeholder. This prevents SQL injection attacks. It treats the `$variable` as a value, not as part of the SQL query. The position or index of the `$variables` should exactly match with `?` placeholder. 

*Example:*
```php
$sql = "SELECT * FROM users WHERE username = ? and active = ?";
$stmt = $pdo->prepare($sql);
$username = $_POST['username'];
$active = true;
$stmt->execute([$username, $active]);
```

- Parameterized Queries:
Another way to execute queries with parameterized queries. This accepts `key` name through associative array that `key` name should exactly match with specific placeholder name. This can also prevent SQL injection attacks.

```php
$username = 'kumar';
$status = true;
$stmt = $pdo->prepare("SELECT * FROM users WHERE username = :username and active = :status");
$stmt->bindParam(':username', $username);
$stmt->bindParam(':status', $status);
$stmt->execute();
```

---
[&#8682; To Top](#-database-abstraction-layers)

[&#10094; Previous Topic](./namespace.md) &emsp; [Next Topic &#10095;](./php-mysql-integration.md)

[&#8962; Goto Home Page](../README.md)