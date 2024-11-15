## &#10162; PHP MySQL Integration:
PHP offer to establish connection to the popular databases. Here, PHP can integrate MySQL database easily for querying data from database.

### &#9780; Overview:
1. [MySQL Overview](#-mysql-overview)
2. [Connecting to a MySQL Database](#-connecting-to-a-mysql-database)
3. [Executing SQL Queries](#-executing-sql-queries)
4. [Updating and Deleting Data](#-updating-and-deleting-data)

### &#10022; MySQL Overview:
MySQL is a popular and open-source relational database management system. It is a reliable, efficient, and flexible database that widely used with PHP to handle a wide range of applications.

Common things for MySQL is Preferable with PHP:
- Community Support: It has an active and large community to provide supports and resources.
- Ease of Use: It is relatively easy to learn and use.
- Open-Source: It is freely available and it can be customized to fit specific requirements.
- Performance: It is known for high performance and scalability.
- Security: It has robust security features to protect sensitive data.

Learn MySQL basics from this [MySQL Notes](https://github.com/ag-sanjjeev/mysql-notes) repository.

### &#10022; Connecting to a MySQL Database:
To connect to a MySQL database in PHP, use either the `MySQLi` extension or `PDO` (PHP Data Objects).

- MySQLi:
```php
// Database credentials
$servername = "localhost";
$username = "username";
$password = "password";
$dbname = "test";

// Establish database connection
$conn = new mysqli($servername, $username, $password, $dbname);

// Check connection
if ($conn->connect_error) {
  die("Connection failed: " . $conn->connect_error);
}

echo "Connected successfully";

// Close the database connection after end of the script
$conn->close();
```

- PDO:
```php
// Database credentials
$dsn = "mysql:host=localhost;dbname=test";
$username = "username";
$password = "password";

// Establish database connection
try {
  $pdo = new PDO($dsn, $username, $password);
  echo "Connected successfully";
} catch (PDOException $e) {
  echo "Connection failed: " . $e->getMessage();
}
```

### &#10022; Executing SQL Queries:

- MySQLi:
```php
// SQL Query
$sql = "SELECT * FROM staff";

// Executing Query
$result = $conn->query($sql);

// Checking for results
if ($result->num_rows > 0) {
  // output the result of each row
  while($row = $result->fetch_assoc()) {
    echo "staff_id: " . $row["staff_id"]. " - First Name: " . $row["first_name"] . "<br>";
  }
} else {
  echo "No record found";
}
```

- PDO:
```php
// SQL Query
$sql = "SELECT * FROM staff";
$stmt = $pdo->prepare($sql);
// Executing Query
$stmt->execute();

// Fetching results
$result = $stmt->fetchAll(PDO::FETCH_ASSOC);

// output the result of each row
foreach ($result as $row) {
    echo "staff_id: " . $row["staff_id"]. " - First Name: " . $row["first_name"] . "<br>";
}
```

### &#10022; Updating and Deleting Data:

- MySQLi:
```php
$sql = "UPDATE staff SET email='user.name@host.com' WHERE staff_id=3";
$conn->query($sql);

$sql = "DELETE FROM users WHERE id=3";
$conn->query($sql);
```

- PDO:
```php
$sql = "UPDATE staff SET email=:email WHERE staff_id=:id";
$stmt = $pdo->prepare($sql);
$stmt->bindParam(':email', $newEmail);
$stmt->bindParam(':id', $userId);
$stmt->execute();

$sql = "DELETE FROM staff WHERE staff_id=:id";
$stmt = $pdo->prepare($sql);
$stmt->bindParam(':id', $userId);
$stmt->execute();
```

---
[&#8682; To Top](#-php-mysql-integration)

[&#10094; Previous Topic](./database-abstraction-layers.md) &emsp; [Next Topic &#10095;](./web-frameworks.md)

[&#8962; Goto Home Page](../README.md)