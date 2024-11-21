## &#10162; Short-Hand Syntax:
PHP offers several shorthand syntax to make code more concise, simple and readable. 

### &#9780; Overview:
1. [Ternary Operator](#-ternary-operator)
2. [Null Coalescing Operator](#-null-coalescing-operator)
3. [Null Coalescing Assignment Operator](#-null-coalescing-assignment-operator)
4. [Short Echo Tag](#-short-echo-tag)
5. [Spaceship Operator](#-spaceship-operator)
6. [Short-Hand Control Structures](#-short-hand-control-structures)

### &#10022; Ternary Operator:
A simplest way to write conditional expressions with ternary operator.

*Syntax:*
```php
$result = $condition ? $value_if_true : $value_if_false;
```

*Example:*
```php
$price = 2500;
$offerInPercentage = ($price >= 2000) ? 20 : 10;
echo $offerInPercentage; // Output: 20
```

### &#10022; Null Coalescing Operator:
Null coalescing operator is `??`. Which is used to easiest way to assign a default value to a variable if it is a null.

*Syntax:*
```php
$value = $variable ?? 'default_value';
```

*Example:*
```php
$name = $_SESSION['user_name'] ?? 'Guest';
echo "Welcome, $name!";
```

### &#10022; Null Coalescing Assignment Operator:
It is denoted as `??=` symbols. This is used to assigns a value to a variable only if it is not already set.

*Syntax:*
```php
$variable ??= 'default_value';
```

*Example:*
```php
$name = isset($_POST['user_name']) ? $_POST['user_name'] : null;
$name ??= 'Guest';
echo "Welcome, $name!";
```

### &#10022; Short Echo Tag:
A shorter way to echo a variable in PHP. This is not always supported by default. But it need to enable in PHP configuration.

*Syntax:*
```php
<?= $variable; ?>
```

*Example:*
```php
<?= 'Hello, world!' ?>
```

### &#10022; Spaceship Operator: 
It is denoted as `<=>` symbols. It compares two values and returns -1, 0, or 1. If a first value is less than a second value, then it will return -1. If both values are equal, then it will return 0. If a first value is greater than a second value, then it will return 1.

*Syntax:*
```php
$result = $a <=> $b;
```

*Example:*
```php
$a = 10;
$b = 5;
$comparison = $a <=> $b; 
echo $comparison; // Output: 1
```

### &#10022; Short-Hand Control Structures:
- Conditional Statements:
```php
// if 
if ($condition):
	// code to be executed if condition is true
endif;
```

```php
// if-else
if ($condition):
	// code to be executed if condition is true
else:
	// code to be executed if condition is false
endif;
```

- Loops:
```php
// while
while ($condition):
	// code to be executed until condition is true
endwhile;
```

```php
// do-while
do:
    // code to be executed first even condition is false
while ($condition);
```

```php
// for
for ($i = 0; $i < 10; $i++):
    // code to be executed until condition is true
endfor;
```

```php
// foreach
foreach ($array as $value):
    // Iterates through $array elements
endforeach;
```

- Switch statement:
```php
// switch
switch ($variable):
    case 'value1':
        // code to be executed if matches this case
        break;
    case 'value2':
        // code to be executed if matches this case
        break;
    default:
        // code to be executed if none of the case matches
endswitch;
```

---
[&#8682; To Top](#-short-hand-syntax)

[&#10094; Previous Topic](./enums.md) &emsp; [Next Topic &#10095;](./type-hints.md)

[&#8962; Goto Home Page](../README.md)