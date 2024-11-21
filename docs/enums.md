## &#10162; Enums:
Enums are also referred as enumerations. Which is a data type that consists of a set of named constants. This is used to define a fixed set of possible values to a variable.

### &#9780; Overview:
1. [Need of Enum](#-need-of-enum)
2. [Enum Implementation](#-enum-implementation)
3. [Backed Enums](#-backed-enums)
4. [Enum Methods](#-enum-methods)
5. [Enum Static Methods](#-enum-static-methods)
6. [Enum Constants](#-enum-constants)
7. [Enum With Traits](#-enum-with-traits)
8. [Enum Serialization](#-enum-serialization)
9. [Enum Usages](#-enum-usages)
10. [Key Points And Limitations](#-key-points-and-limitations)

### &#10022; Need of Enum:
- Type Safety: It provides type safety for a variable by holding defined values.
- Readability: It make code more readable by using descriptive names for constants.
- Reduced Errors: It can help to prevent invalid values.

### &#10022; Enum Implementation:
*Syntax:*
```php
enum ConstantName {
    case ValueName1;
    case ValueName2;
    case ValueName3;
}

$var = ConstantName::ValueName1;
```

### &#10022; Backed Enums:
*Syntax:*
```php
enum ConstantName: string {
    case ValueName1='value1';
    case ValueName2='value2';
    case ValueName3='value3';
}

$var = ConstantName::ValueName1->value;
```

### &#10022; Enum Methods:
It can hold methods like classes.
```php
interface HTTPStatusInterface {
    public function getStatusCode();
}

enum HTTPStatus implements HTTPStatusInterface {
    case OK;
    case NotFound;
    case InternalServerError;

    public function getStatusCode(): int
    {
        return match($this) {
            HTTPStatus::OK => 200,
            HTTPStatus::NotFound => 404,
            HTTPStatus::InternalServerError => 500
        };
    }
}

echo HTTPStatus::OK->getStatusCode();
```

### &#10022; Enum Static Methods:
It can holds static methods like classes.

```php

interface HTTPStatusInterface {
    public static function getStatusCode($status);
}

enum HTTPStatus implements HTTPStatusInterface {
    case OK;
    case NotFound;
    case InternalServerError;

    public static function getStatusCode($status): static
    {
        return match(true) {
            $status == 200 => static::OK,
            $status == 404 => static::NotFound,
            $status == 500 => static::InternalServerError
        };
    }
}

echo HTTPStatus::getStatusCode(200)->name;
```

### &#10022; Enum Constants:
Enum can hold constants with an access modifiers such as a `private`, `protected` and `public`.

```php
enum Product {
    case Shirt;
    case Pant;

    public const MediumShirt = Size::Medium;
    public const LargePant = Size::Large;
}

enum Size {
    case Small;
    case Medium;
    case Large;

    public const SmallSize = 36;
    public const MediumSize = 40;
    public const LargeSize = 46;
}

print Product::Pant::MediumShirt->name . PHP_EOL;

print Product::Pant::MediumShirt::MediumSize;
```

### &#10022; Enum With Traits:
Enum can use trait same as class behavior.

```php
trait PriceTrait {
    public function calculatePrice($size): int
    {
        return match(true) {
            ($this == static::Shirt && $size == Size::Small) => 100, 
            ($this == static::Shirt && $size == Size::Medium) => 120, 
            ($this == static::Shirt && $size == Size::Large) => 140,
            ($this == static::Pant && $size == Size::Small) => 150, 
            ($this == static::Pant && $size == Size::Medium) => 170, 
            ($this == static::Pant && $size == Size::Large) => 190, 
        };
    }
} 

enum Product {
    use PriceTrait;
    case Shirt;
    case Pant;
}

enum Size {
    case Small;
    case Medium;
    case Large;
}

print Product::Shirt->calculatePrice(Size::Small);
```

### &#10022; Enum Serialization:
Enum can be serialized into string and unserialized back into original form.

```php
enum SizeOptions: int {
    case Small = 36;
    case Medium = 40;
    case Large = 46;
}

print serialize(SizeOptions::cases());
print_r(unserialize(serialize(SizeOptions::cases())));
```

### &#10022; Enum Usages:
- Enums can be used as type hints for function parameters and their return types. 
- Enums can be used in switch statements for concise and type-safe comparisons.
- Enums can be compared using comparison operators.
- Enums can iterate over enum cases using loops such as `foreach` and `while`.


*Example:*
```php
enum HTTPStatus: int {
    case OK = 200;
    case NotFound = 404;
    case InternalServerError = 500;
}

$statusCode = HTTPStatus::NotFound;
echo $statusCode->value; // Output: 404
```

*Example:*
```php
enum HTTPStatus {
    case OK;
    case NotFound;
    case InternalServerError;
}

function getStatusCode(HTTPStatus $status): int {
    return match ($status) {
        HTTPStatus::OK => 200,
        HTTPStatus::NotFound => 404,
        HTTPStatus::InternalServerError => 500
    };
}

echo getStatusCode(HTTPStatus::OK);
```

*Example:*
```php
enum SortOrder {
	case Asc;
	case Desc;
}

DB::select("name")->fetchAll(SortOrder::Desc);
```

*Example:*
```php
enum SizeOptions: int {
    case Small = 36;
    case Medium = 40;
    case Large = 46;
}
print "<label>Size</label> <br>";
print "<select name=\"size\">";
foreach (SizeOptions::cases() as $case) {
    print "<option value=\"" . $case->value . "\">" . $case->name . "</option>";
}
print "</select>";
```

### &#10022; Key Points And Limitations:
**Key Points:**
- It is a case-insensitive.
- Enum cases can associate values.
- Enums can be backed by values such as integers or strings.
- Enums can be defined and marked as unit-safe to prevent unintentional type conversions.

**Limitations:**
- Enum can support in PHP from 8.1 and later versions.
- Enum behave like classes, But it cannot be instantiated with `new` keyword like classes.
- It cannot be extended with `extend` keyword like classes.

---
[&#8682; To Top](#-enums)

[&#10094; Previous Topic](./arrays.md) &emsp; [Next Topic &#10095;](./short-hand-syntax.md)

[&#8962; Goto Home Page](../README.md)