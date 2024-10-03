## &#10162; Functions:
Functions are blocks of code that perform specific tasks. That promote code re-usability, code modularity and improve maintainability.

### &#9780; Overview:
1. [Function Definition]
2. [Function Calling]
3. [Function Arguments and Parameters]
4. [Function Return Values]
5. [Pass by Value]
6. [Pass by Reference]
7. [Scope of Variables]
8. [Variable Length Argument Lists]
9. [Anonymous Functions]
10. [Recursion]
11. [Variable Functions]

### &#10022; Function Definition:
It means creating function by defining the details.

*Syntax:*
```php
function functionName(argument1, argument2, ...) { // Arguments are optional
  // Block of code
  return returnValue; // Return value is optional
}
```

### &#10022; Function Calling:
It executes a block of code which is defined as function, To call by their `functionName` followed by parentheses to pass parameters if any arguments are defined.

*Syntax:*
```php
functionName(parameter1, parameter2, ...);
```

*Example:*
```php
function greet($name) {
  echo "Good Morning, $name!";
}

greet("Kumar"); // Outputs "Good Morning, Kumar!"
```

### &#10022; Function Arguments and Parameters:
- **Arguments:** are values that accept by a function when calling it. These arguments treated as input data for the function to work with their logic. Arguments are defined as one by one separated by a comma `,` and listed within parentheses after the function name. This is technical term used in function definition.

- **Parameters:** are values that pass to a function when calling it. This is technical term used in function call.

*Function arguments and function parameters are same, but differs by the place of usage.*

### &#10022; Function Return Values:
The function may return some useful response as a output at the end of the function execution. The `return` statement in a block of function code that allows a function to end their execution at the place where it is mentioned and send a value back to the place where the function was called. 

*Syntax: `return returnValue;`*


*Example:*
```php
function addNumbers($num1, $num2) {
  $sum = $num1 + $num2;
  return $sum; // end of execution and returns the value
}

$result = addNumbers(10, 5);
echo $result; // Outputs 15
```

### &#10022; Pass by Value:
Function arguments has two mechanism. The one is, the function handles the arguments by the value has passed to it. That value is a copy of the parameter value is passed to the function. Any modifications made on the arguments value within the function that affects only the copy, but not the original variable outside the function.

```php
function updateString($text) {
  $text = "Modified message";
}

$message = "Original message";
updateString($message);
echo $message; // Outputs "Original message" (original string remains unchanged)
```

### &#10022; Pass by Reference:
Function arguments has two mechanism. The another one is, the function handles the arguments by the reference of the value, which means exact memory location of the value. This allows the function to directly modify the original variable if any modification takes places and that reflect the outside of the function.

*Syntax: Ampersand symbol (`&`) before an argument in a function definition.*

```php
function incrementOne(&$number) {
  $number++;
}

$x = 5;
incrementOne($x);
echo $x; // Outputs 6 (original variable is modified)
```

### &#10022; Scope of Variables
It decides the visibility of a variable within the program. 
	- Variables declared inside a function blocks, that have local scope. Which means accessible within function block. 
	- Variables declared outside of function blocks, that have global scope. Which means accessible throughout of the script.

*Example:*
```php
$globalVariable = "This is a global variable";

function showScope() {
  $localVariable = "This is a local variable";
  echo "Inside function: $localVariable, $globalVariable <br>";
}

showScope();
echo "Outside function: $localVariable, $globalVariable"; // Local variable not accessible
```

### &#10022; Variable Length Argument Lists
To get list of arguments that the passed to the function when it called by the function `func_get_args()`.

*Example:*
```php
function myFunction() {
    $args = func_get_args();
    foreach ($args as $arg) {
        echo $arg . "\n";
    }
}

myFunction("Good", "Morning", 123);
```

### &#10022; Anonymous Functions:
It is used to create anonymous functions on the go within the script by simple definition without function name.

*Example:*
```php
// Anonymous function definition
$greet = function($name) {
    echo "Good Morning, $name!";
};

// function call
$greet("Kumar");
```

### &#10022; Recursion
To Calling a function within itself again and again for solving problems that can be broken down into smaller or similar subproblems.

*Example:*
```php
function factorial($n) {
    if ($n === 0) {
        return 1;
    } else {
        return $n * factorial($n - 1);
    }
}

echo factorial(5); // Outputs 120
```

### &#10022; Variable Functions
To call dynamically a specific function based the value of the variable. It is also referred as function aliasing. To assign different names for an existing function.

*Example:*
```php
$functionName = "greet";
$functionName(); // this refers to the function name and call 

function greet() {
    echo "Good Morning";
}
```

---
[&#8682; To Top](#-functions)

[&#10094; Previous Topic](./control-flow.md) &emsp; [Next Topic &#10095;](./arrays.md)

[&#8962; Goto Home Page](../README.md)