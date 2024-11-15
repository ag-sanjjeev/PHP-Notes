## &#10162; Regular Expressions:
Regular expressions also known as Regex. These are a powerful tool used for pattern matching and text manipulation. It provide a flexible way to find, replace, and validate text or strings.

### &#9780; Overview:
1. [Pattern Matching](#-pattern-matching)
2. [Find and Replacing Text](#-find-and-replacing-text)
3. [Extracting Text](#-extracting-text)
4. [Validate Text](#-validate-text)
5. [Common Patterns](#-common-patterns)

### &#10022; Pattern Matching:
It used to match given or specific patterns within a string.

```php
$string = "The sample text paragraph with some few words in the line.";
$pattern = "/sample text/";

if (preg_match($pattern, $string)) {
    echo "Match found!";
}
```

```php
$pattern = "/\d{3}-\d{4}-\d{2}/";
$string = "Phone number: 123-4567-89.";

if (preg_match($pattern, $string, $matches)) {
    echo "Extracted Phone number: " . $matches[0];
} else {
    echo "No match found";
}
```

### &#10022; Find and Replacing Text:
To find and replace the given text using regular expression.

```php
$string = "The sample text paragraph with some few words in the line.";
$newString = preg_replace("/few/", "more", $string);
echo $newString; // Output: The sample text paragraph with some more words in the line.
```

### &#10022; Extracting Text:
- To extract specific part of the text from given string.

```php
$string = "Kumara Vel (kumaravel@host.com)";
preg_match("/\((.*)\)/", $string, $matches);
echo $matches[1]; // Output: kumaravel@host.com
```

- To match and extract all text from given string.

```php
$string = "The sample text paragraph with sample few words in the line.";
preg_match_all("/sample/", $string, $matches);
print_r($matches);
```

- To split text with given pattern.

```php
$string = "apple, banana, orange";
$pattern = "/, /";
$fruits = preg_split($pattern, $string);
print_r($fruits);
``` 

### &#10022; Validate Text:
To check or validate text in given format.

```php
$email = "kumaravel@host.com";
if (preg_match("/^\w+@\w+\.\w+$/", $email)) {
    echo "Valid email address";
} else {
    echo "Invalid email address";
}
```

### &#10022; Common Patterns:
- Character Classes:
  - `[abc]`: Matches any single character from the set.
  - `[^abc]`: Matches any single character not in the set.
  - `[a-z]`: Matches any lowercase letter.
  - `[A-Z]`: Matches any uppercase letter.
  - `[0-9]`: Matches any digit.
- Quantifiers: 
  - `+`: Matches one or more repetitions of the preceding element.
  - `*`: Matches zero or more repetitions of the preceding element.
  - `?`: Matches zero or one repetition of the preceding element.
  - `{n}`: Matches exactly n repetitions.
  - `{n,}`: Matches at least n repetitions.
  - `{n,m}`: Matches at least n and at most m repetitions.
- Anchors:
 	- `^`: Matches the beginning of the string.
  - `$`: Matches the end of the string. 
- Grouping:
	- `()`: Groups a part of the pattern.
	- `{}`: Matches a specific number of occurrences of the preceding element.
	- `[]`: Matches a character within the specified set.
- Alternative:
	- `|`: Matches either the expression before or after the symbol.
- Metacharacters: 
	- `.` : Matches any single character except a newline.
	- `\d`: Matches a digit character.
	- `\d{2}`: Matches a two digit character.
	- `\d+`: Matches a multiple digit character.
  - `\w`: Matches any word character (alphanumeric or underscore).
  - `\w{5}`: Matches a five letter word.
  - `\w+`: Matches a multiple character word.
  - `\W`: Matches any non-word character.
  - `\s`: Matches any whitespace character.
  - `\S`: Matches any non-whitespace character.

---
[&#8682; To Top](#-regular-expressions)

[&#10094; Previous Topic](./security-best-practices.md) &emsp; [Next Topic &#10095;](./xml-and-json.md)

[&#8962; Goto Home Page](../README.md)