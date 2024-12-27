## &#10162; Functions:
Functions are blocks of code that perform specific tasks. That promote code re-usability, code modularity and improve maintainability.

### &#9780; Overview:
1. [Function Definition](#-function-definition)
2. [Function Calling](#-function-calling)
3. [Function Arguments and Parameters](#-function-arguments-and-parameters)
4. [Function Return Values](#-function-return-values)
5. [Pass by Value](#-pass-by-value)
6. [Pass by Reference](#-pass-by-reference)
7. [Scope of Variables](#-scope-of-variables)
8. [Variable Length Argument Lists](#-variable-length-argument-lists)
9. [Anonymous Functions](#-anonymous-functions)
10. [Recursion](#-recursion)
11. [Variable Functions](#-variable-functions)
12. [Type Hinting](#-type-hinting)
13. [Return Type Declarations](#-return-type-declarations)
14. [Generators](#-generators)
15. [Arrow Functions](#-arrow-functions)
16. [String Functions](#-string-functions)
17. [Mathematical Functions](#-mathematical-functions)
18. [Date and Time Functions](#-date-and-time-functions)
19. [File and Directory Functions](#-file-and-directory-functions)
20. [Array Functions](#-array-functions)
21. [Other Common Functions](#-other-common-functions)

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

### &#10022; Scope of Variables:
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

### &#10022; Variable Length Argument Lists:
To get list of arguments that the passed to the function when it called by the function `func_get_args()` and get number of arguments that passed to the function by `func_num_args()` methods.

*Example:*
```php
function myFunction() {
    $args = func_get_args();
    $argsCount = func_num_args();
    foreach ($args as $arg) {
        echo $arg . "&nbsp;";
    }
    echo "<br> Total arguments passed : $argsCount";
}

myFunction("Good", "Morning", 123);
```

To get `n` number of arguments as array by using variable length arguments.

*Example:*
```php
function sum(...$numbers) { 
  return array_sum($numbers);
}

$result = sum(1, 2, 3, 4, 5);
echo $result; // Outputs 15
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

### &#10022; Recursion:
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

### &#10022; Variable Functions:
To call dynamically a specific function based the value of the variable. It is also referred as function aliasing. To assign different names for an existing function.

*Example:*
```php
$functionName = "greet";
$functionName(); // this refers to the function name and call 

function greet() {
    echo "Good Morning";
}
```

### &#10022; Type Hinting:
It is useful to specifying the expected argument type.

*Example:*
```php
function addNumbers(int $a, int $b) {
  return $a + $b;
}
```

### &#10022; Return Type Declarations:
It typecast the data which is return from a function.

*Example:*
```php
function addNumbers(float $a, float $b): int {
    return $a + $b;
}
```

### &#10022; Generators:
It returns the value one at a time using `yield` keyword. This is useful for large datasets and infinite sequence. 

*Example:*
```php
// generators
function generateNumbers() {
  for ($i = 1; $i <= 5; $i++) {
    yield $i;
  }
}

foreach (generateNumbers() as $number) {
  echo $number . PHP_EOL;
}
```

### &#10022; Arrow Functions:
To create function definition in simpler way and used in the function parameters as a callback. It also know as arrow function in PHP.

*Example:*
```php
$numbers = [1, 2, 3, 4, 5];

// arrow function
$squareOfNumbers = array_map(fn ($num) => $num * $num, $numbers);

print_r($squareOfNumbers);
```

### &#10022; String Functions:

- `strlen()`: Returns the length or number of characters in a string.
- `str_replace()`: Replaces occurrences of one string with another.
- `strpos()`: Returns the position or index of the first occurrence of a substring within a string.
- `strtoupper()`: Converts a string to uppercase.
- `strtolower()`: Converts a string to lowercase.
- `trim()`: Removes whitespace from the beginning and end of a string.
- `explode()`: Splits a string into an array of substrings by the separator.
- `implode()`: Joins elements of an array into a string with the separator.

### &#10022; Mathematical Functions:

- `abs()`: Returns the absolute value of a number.
- `round()`: Rounds a floating-point number to the nearest integer.
- `ceil()`: Rounds a floating-point number up to the nearest integer.
- `floor()`: Rounds a floating-point number down to the nearest integer.
- `sqrt()`: Calculates the square root of a number.
- `pow()`: Raises a number to a power.
- `sin()`, `cos()`, `tan()`, etc.: Trigonometric functions.
- `rand()`: Generates a random integer within a specified range.

### &#10022; Date and Time Functions:

- `date()`: Returns a timestamp into a human-readable date and time string based on given format.
- `time()`: Returns the current time in seconds since the Unix epoch.
- `strtotime()`: Converts a human-readable date and time string into a Unix timestamp.
- `mktime()`: Creates a Unix timestamp from specified date and time.

### &#10022; File and Directory Functions:

- `file_exists()`: Checks if a file or directory exists.
- `fopen()`: Opens a file.
- `fclose()`: Closes a file.
- `fread()`: Reads data from a file.
- `fwrite()`: Writes data to a file.
- `file_get_contents()`: Reads the contents of a file into a string.
- `file_put_contents()`: Writes data to a file.
- `mkdir()`: Creates a directory.
- `rmdir()`: Deletes a directory.

### &#10022; Array Functions:

- `count()`: Returns the number of elements in an array.
- `array_push()`: Adds elements to the end of an array.
- `array_pop()`: Removes the last element from an array and returns it.
- `array_shift()`: Removes the first element from an array and returns it.
- `array_unshift()`: Adds elements to the beginning of an array.
- `array_keys()`: Returns an array containing the keys from an associative array.
- `array_values()`: Returns an array containing the values from an associative array.

### &#10022; Other Common Functions:

- `is_array()`: Checks if a variable is an array.
- `is_string()`: Checks if a variable is a string.
- `is_numeric()`: Checks if a variable is numeric.
- `empty()`: Checks if a variable is empty.
- `isset()`: Checks if a variable is set or exist.
- `json_encode()`: Encodes a PHP value to JSON.
- `json_decode()`: Decodes a JSON string into a PHP value.
- `var_dump()`: Dumps information about a variable.
- `print_r()`: Prints a human-readable representation of a variable.
- `die()`: Stops the execution of the script and optionally displays a message.

---
[&#8682; To Top](#-functions)

[&#10094; Previous Topic](./control-flow.md) &emsp; [Next Topic &#10095;](./arrays.md)

[&#8962; Goto Home Page](../README.md)