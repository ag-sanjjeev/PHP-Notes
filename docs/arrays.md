## &#10162; Arrays:
Arrays are fundamental data structures in PHP. It allows to store and manage collections and series of items under a single variable name. 

### &#9780; Overview:
1. [Array Types](#-array-types)
2. [Indexed Array](#-indexed-array)
3. [Associative Array](#-associative-array)
4. [Multi Dimensional Array](#-multi-dimensional-array)
5. [Choosing Array](#-choosing-array)
6. [Adding Elements in Array](#-adding-elements-in-array)
7. [Accessing Array Elements](#-accessing-array-elements)
8. [Array Elements Unpack](#-array-elements-unpack)
9. [Iterating Array Elements](#-iterating-array-elements)
10. [Common Array Functions](#-common-array-functions)


### &#10022; Array Types:
PHP has 3 types of arrays.
  1. [Indexed Array](#-indexed-array)
  2. [Associative Array](#-associative-array)
  3. [Multi Dimensional Array](#-multi-dimensional-array)

### &#10022; Indexed Array:
This indexed arrays are holding collection of items in ordered manner, where each item is accessed by a numerical index starting from 0.

*Example:*
```php
$fruits = ["apple", "banana", "orange"];

echo $fruits[0]; 
// Outputs "apple"
echo $fruits[2]; 
// Outputs "orange"
```

### &#10022; Associative Array:
This associative arrays are also known as Hashes, these arrays items are stored as key-value pairs. The item can be accessed using their unique keys instead of numerical indexes.

*Example:*
```php
$grocery = [
  "fruit" => "banana",
  "vegetable" => "cauliflower"  
];

echo $grocery["fruit"]; 
// Outputs "banana"
echo $grocery["vegetable"]; 
// Outputs "cauliflower"
```

### &#10022; Multi Dimensional Array:
If an array holds an another array, then it is known as multi dimensional array. That represents the array items in a multi dimensional structure. and it is useful for complex data sets and nested elements. It may either indexed array or associative array.

*Example:*
```php
$products = [
  [
    "name" => "Shirt",
    "price" => 300.00,
    "size" => ["S", "M", "L", "XL"]
  ],
  [
    "name" => "Pants",
    "price" => 450.00,
    "size" => ["S", "M", "L", "XL", "XXL"]
  ]
];

echo $products[0]["size"][2]; 
// Outputs "L" (size at index 2 of product 0)
```

### &#10022; Choosing Array
- Indexed arrays: when there is a need for storing the elements in an ordered and sequential.
- Associative arrays: when there is a need for storing the elements with identification and access elements by specific names.

### &#10022; Adding Elements in Array:
To add elements to existing array by using their array reference.

*Syntax: `$array1[] = $element;`*

*Example:*
```php
$fruits = ["apple", "banana"];
// adding array elements
$fruits[] = "orange";
print_r($fruits); 
// Output: Array ( [0] => apple [1] => banana [2] => orange )
```

### &#10022; Accessing Array Elements:
Accessing array elements by specifying their index and key name in the series of square brackets.

*Example:*
```php
$grocery = [
    ["name" => "Mango", "price" => 100],
    ["name" => "Pineapple", "grade" => 150]
];

echo $grocery[0]["name"]; 
// Output: Mango
```

### &#10022; Array Elements Unpack:
It allows to unpack elements of array into individual variables.

*Syntax: `list($variable1,...) = $array1;`*

*Example:*
```php
$person = ["Kumar", 30];
list($name, $age) = $person;

echo $name; 
// Output: Kumar
echo $age; 
// Output: 30
```

To unpack array elements into individual parameter during function call.

*Syntax: `functionName(...$array1);`*

*Example:*
```php
function sum($a, $b) {
  return $a + $b;
}

$numbers = [1, 2];
$result = sum(...$numbers); 
// Unpacking array elements
echo $result; 
// Output: 3
```

### &#10022; Iterating Array Elements:
Iterate array elements with array iterator class.

*Example: Using `foreach` loop*
```php
$array = ["apple", "banana", "orange"];
$iterator = new ArrayIterator($array);

foreach ($iterator as $value) {
  echo $value . PHP_EOL;
}
```

*Example: Using `array_walk` function*
It iterates through one dimension level.

```php
$grocery = [
    ["name" => "Mango", "price" => 100],
    ["name" => "Pineapple", "price" => 150]
];

array_walk($grocery, 'groceryItems');

function groceryItems($value) 
{
  print_r($value);
}
```

*Example: Using `array_walk_recursive` function*
It iterates through multi dimensional level in one by one. It pass parameters to the function as named parameter such as `$key` and `$value`.

```php
$grocery = [
    ["name" => "Mango", "price" => ["grade1" => 100, "grade2" => 200]],
    ["name" => "Pineapple", "price" => 150]
];

array_walk_recursive($grocery, 'groceryItems');
array_walk_recursive($grocery, 'groceryItemsValue');


// groceryItems($value, $key) also valid due to named parameters
function groceryItems($key, $value) 
{
  echo $key . PHP_EOL . $value . PHP_EOL;
}

function groceryItemsValue($value) 
{
  echo $value . PHP_EOL;
}
```

### &#10022; Common Array Functions:
PHP provides a rich set of functions to manipulate and interact with arrays. Here are some commonly used functions:
- Sorting:
  - `sort()`: Sorts an array elements in ascending order.
    ```php
    $numbers = [5, 3, 6, 8, 4];
    sort($numbers);
    print_r($numbers); 
    // Output: 3, 4, 5, 6, 8
    ```
  - `rsort()`: Sorts an array elements in descending order.
    ```php
    $numbers = [5, 3, 6, 8, 4];
    rsort($numbers);
    print_r($numbers); 
    // Output: 3, 4, 5, 6, 8
    ```
  - `asort()`: Sorts an array elements and maintaining key-value associations in ascending order.
    ```php
    $fruits = ["apple" => 90, "banana" => 10, "orange" => 50];
    asort($fruits);
    print_r($fruits); 
    // Output: Array ( [banana] => 10 [orange] => 50 [apple] => 90 )
    ```
  - `usort()`: Sorts an array by user-defined comparison function.
    ```php
    function compare_by_length($a, $b) {
        return strlen($a) - strlen($b);
    }

    $fruits = ["banana", "apple", "strawberry", "orange"];
    usort($fruits, "compare_by_length");
    print_r($fruits); 
    // Output: Array ( [0] => apple [1] => banana [2] => orange [3] => strawberry )
    ```
  - `uasort()`: Sorts an associative array by value, maintaining index association.
    ```php
    $fruits = ["apple" => 90, "banana" => 10, "orange" => 50];
    // sort fruit with price
    uasort($fruits, function($a, $b) {
        return $a - $b;
    });
    print_r($fruits); 
    // Output: Array ( [banana] => 10 [orange] => 50 [apple] => 90 )
    ```
  - `uksort()`: Sorts an associative array by keys.
    ```php
    $fruits = ["apple" => 90, "banana" => 10, "orange" => 50];
    uksort($fruits, function($a, $b) {
        return strcmp($a, $b);
    });
    print_r($fruits); 
    // Output: Array ( [apple] => 90 [banana] => 10 [orange] => 50 )
    ```
- Searching:
  - `array_key_exists()`: Checks if array key exist in associative array.
    ```php
    $person = array("name" => "kumar", "age" => 30);
    if (array_key_exists("name", $person)) {
        echo "Array key 'name' exists.";
    } else {
        echo "Array key 'name' does not exist.";
    }
    ```
  - `in_array($value, $array)`: Checks if a value exists in an array.
    ```php
    $fruits = array("apple", "banana", "orange");
    $find = "banana";
    if (in_array($find, $fruits)) {
        echo "$find is in the array.";
    } else {
        echo "$find is not in the array.";
    }
    ```
  - `array_search($value, $array)`: Returns the index of the value at first occurrence in an array.
    ```php
    $numbers = [1, 2, 3, 4, 5, 6];
    $find = 10;
    $index = array_search($find, $numbers);
    if ($index !== false) {
        echo "$find is found at index $index";
    } else {
        echo "$find is not found in the array";
    }
    ```
  - `array_diff()`: Finds the difference between two given arrays.
    ```php
    $numbers1 = [1, 2, 3, 4, 5, 6];
    $numbers2 = [2, 5, 7, 9];
    $diff = array_diff($numbers1, $numbers2);
    print_r($diff); 
    // Output: Array ( [0] => 1 [2] => 3 [3] => 4 [5] => 6 )
    ```
- Manipulation:
  - `array_pop()`: Removes and returns the last element of an array.
    ```php
    $fruits = ['apple', 'banana', 'orange', 'strawberry'];
    // Remove the last element
    $lastFruit = array_pop($fruits);
    echo $lastFruit; 
    // Output: strawberry
    print_r($fruits); 
    // Output: Array ( [0] => apple [1] => banana [2] => orange )
    ```
  - `array_shift()`: Removes and returns the first element of an array.
    ```php
    $fruits = ['apple', 'banana', 'orange', 'strawberry'];
    // Remove the first element
    $firstFruit = array_shift($fruits);
    echo $firstFruit; 
    // Output: apple
    print_r($fruits); 
    // Output: Array ( [0] => banana [1] => orange [2] => strawberry )
    ```
  - `array_merge()`: Merges two arrays in to a single array
    ```php
    $array1 = ['a', 'b', 'c'];
    $array2 = [1, 2, 3];
    $mergedArray = array_merge($array1, $array2);
    print_r($mergedArray); 
    // Output: Array ( [0] => a [1] => b [2] => c [3] => 1 [4] => 2 [5] => 3 )
    ```
  - `array_combine()`: Combines two arrays into an associative array.
    ```php
    $keys = ['name', 'age', 'nationality'];
    $values = ['Kumar', 30, 'India'];
    $person = array_combine($keys, $values);
    print_r($person); 
    // Output: Array ( [name] => Kumar [age] => 30 [nationality] => India )
    ```
  - `array_slice()`: Extracts a portion of an array.
    ```php
    $numbers = [1, 2, 3, 4, 5, 6];
    // Start at index 2, take 3 elements
    $slicedArray = array_slice($numbers, 2, 3); 
    print_r($slicedArray); 
    // Output: Array ( [0] => 3 [1] => 4 [2] => 5 )
    ```
  - `count($array)`: Returns the number of elements in an array.
    ```php
    $fruits = ['apple', 'banana', 'orange', 'strawberry'];
    $count = count($fruits);
    echo $count; // Output: 4
    ```
  - `array_keys()`: Returns an array of all keys from an associative array.
    ```php
    $person = ['name' => 'Kumar', 'age' => 30, 'nationality' => 'India'];
    $keys = array_keys($person);
    print_r($keys); 
    // Output: Array ( [0] => name [1] => age [2] => nationality ) 
    ```
  - `array_values()`: Returns an array of all values from an associative array.
    ```php
    $person = ['name' => 'Kumar', 'age' => 30, 'nationality' => 'India'];
    $values = array_values($person);
    print_r($values); 
    // Output: Array ( [0] => Kumar [1] => 30 [2] => India )
    ```
  - `array_map()`: Applies a function to each element of an array and returns as a new array.
    ```php
    $numbers = [1, 2, 3, 4, 5];
    $squareOfNumbers = array_map(function($num) {
        return $num * $num;
    }, $numbers);
    print_r($squareOfNumbers);
    ```
  - `array_filter()`: Filters an array elements based on a callback function.
    ```php
    $numbers = [1, 2, 3, 4, 5, 6];
    $evenNumbers = array_filter($numbers, function($n) {
        return $n % 2 === 0;
    });
    print_r($evenNumbers); 
    // Output: Array ( [1] => 2 [3] => 4 [5] => 6 )
    ```
  - `array_reduce()`: Reduces an array to a single value by applying a callback function to each element of an array.
    ```php
    $numbers = [1, 2, 3, 4, 5, 6];
    $sum = array_reduce($numbers, function($carry, $item) {
        return $carry + $item;
    });
    echo $sum; // Output: 21
    ```
  - `array_chunk()`: Divides an array into chunks of a specified size.
    ```php
    $numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9];
    $chunkedArray = array_chunk($numbers, 4);
    print_r($chunkedArray); 
    /* 
    Output: 
    Array ( 
      [0] => Array ( [0] => 1 [1] => 2 [2] => 3 [3] => 4 ) 
      [1] => Array ( [0] => 5 [1] => 6 [2] => 7 [3] => 8 ) 
      [2] => Array ( [0] => 9 ) 
    )
    */
    ```
  - `array_unique()`: Removes duplicate values from an array without affecting index keys.
    ```php
    $numbers = [1, 2, 1, 3, 5, 6, 2, 4, 3, 5];
    $uniqueNumbers = array_unique($numbers);
    print_r($uniqueNumbers); 
    // Output: Array ( [0] => 1 [1] => 2 [3] => 3 [4] => 5 [5] => 6 [7] => 4 )
    ```
  - `array_flip()`: Reverses the keys and values of an associative array.
    ```php
    $fruits = ['apple' => 1, 'banana' => 2, 'orange' => 3, 'strawberry' => 2];
    $flippedFruits = array_flip($fruits);
    print_r($flippedFruits); 
    // Output: Array ( [1] => apple [2] => strawberry [3] => orange )
    ```
  - `array_count_values()`: Counts the occurrences of values in an array.
    ```php
    $numbers = [1, 2, 3, 1, 2, 4, 1];
    $counts = array_count_values($numbers);
    print_r($counts); 
    // Output: Array ( [1] => 3 [2] => 2 [3] => 1 [4] => 1 )
    ```
  - `array_fill()`: Fills an array with a specified value.
    ```php
    $filledArray = array_fill(0, 2, 'fruit');
    print_r($filledArray); 
    // Output: Array ( [0] => fruit [1] => fruit )
    ```

---
[&#8682; To Top](#-arrays)

[&#10094; Previous Topic](./functions.md) &emsp; [Next Topic &#10095;](./short-hand-syntax.md)

[&#8962; Goto Home Page](../README.md)