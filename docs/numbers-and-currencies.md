## &#10162; Numbers and Currencies:
PHP can handle and format numbers as well as currencies in different ways.

### &#9780; Overview:
1. [Number Formats](#-number-formats)
2. [Currency Formats](#-currency-formats)

### &#10022; Number Formats:
PHP provides various functions to format the numbers.

- `number_format()` function:

This function formats a number with grouped thousands separators.

*Syntax:*

`number_format(number, decimal_places, decimal_separator, thousands_separator);`
- `number`: It is a first parameter as a number to format.
- `decimal_places`: It is second and optional parameter as a number of decimal places.
- `decimal_separator`: It is third and optional parameter as a decimal separator character.
- `thousands_separator`: It is fourth and optional parameter as a thousands separator character.

*Example:*
```php
$number = 1234567.89;
$formatted_number = number_format($number, 2, '.', ',');
echo $formatted_number; // Output: 1,234,567.89
```

- `sprintf()` function:

This function provides more flexible with various formatting options using format specifiers.

*Example:*
```php
$number = 1234567.89;
$formatted_number = sprintf("%.2f", $number);
echo $formatted_number; // Output: 1234567.89
```

Refer format specifier in [display statements](./display-statements.md).

### &#10022; Currency Formats:
PHP provides various functions to format the currencies.

- `money_format()` function:

This function formats a number as a currency value by considering the locale settings. But it remove after PHP version `7.0`.

- `NumberFormatter` class:

This provides more advanced formatting capabilities for numbers including currency formatting.

*Example:*
```php
$formatter = new NumberFormatter('en_US', NumberFormatter::CURRENCY);
$formatted_amount = $formatter->formatCurrency(1234.56, 'USD');
echo $formatted_amount; // Output: $1,234.56
```

---
[&#8682; To Top](#-numbers-and-currencies)

[&#10094; Previous Topic](./date-and-time.md) &emsp; [Next Topic &#10095;](./headers.md)

[&#8962; Goto Home Page](../README.md)
