## &#10162; Control Flow:
Control flow statements decides the execution flow of the PHP program based on certain conditions.

### &#9780; Overview:
1. [If Else Statements](#-if-else-statements)
2. [Nested If Else Statements](#-nested-if-else-statements)
3. [Switch Statements](#-switch-statements)

### &#10022; If Else Statements:
This `if..else` statements will allow to execute the code based on the specified condition is true or false.

*Syntax:* 
```php
if (condition) {
  // Code to be executed if the condition is true
} else {
  // Code to be executed if the condition is false
}
```

*Example:*
```php
$age = 30;

if ($age >= 18) {
  echo "You are eligible to cast your vote";
} else {
  echo "You are not eligible to cast your vote";
}
```

### &#10022; Nested If Else Statements:
It implements the complex control flow of the PHP program with the help of nested `if..else` statements.

*Example:*
```php
$price = 2000;

if ($price > 2000) {
  echo "You have discount of 25%";
} else if ($price < 2000 && $price > 1000) {
  echo "You have discount of 10%";
} else {
  echo "No discount eligible";
}
```

### &#10022; Switch Statements:
It provides simplest way to handle and switch to desired condition among multiple conditions with same variable.

*Syntax:*
```php
switch (expression) {
  case value1:
    // Code to execute if the expression equals to value1
    break;
  case value2:
    // Code to execute if the expression equals to value2
    break;
  // more cases if necessary
  default:
    // Code to execute if the no match found for the expression (optional)
  	break;
}
```

*Example:*
```php
$day = 'monday';

switch ($day) {
	case 'monday':
		echo "Monday is weekday";
		break;

	case 'tuesday':
		echo "Tuesday is weekday";
		break;

	case 'wednesday':
		echo "Wednesday is weekday";
		break;

	case 'thursday':
		echo "Thursday is weekday";
		break;

	case 'friday':
		echo "Friday is weekday";
		break;
	
	default:
		echo "Saturday and Sunday are weekends";
		break;
}
```

---
[&#8682; To Top](#-control-flow)

[&#10094; Previous Topic](./basic-syntax.md) &emsp; [Next Topic &#10095;](./functions.md)

[&#8962; Goto Home Page](../README.md)