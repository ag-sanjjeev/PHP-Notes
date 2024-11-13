## &#10162; XML and JSON:
XML and JSON are file formats that used to store and exchange data as per requirements.
XML stands for Extensible Markup Language. XML supports information exchange between computer systems.
JSON stands for JavaScript Object Notation. JSON is independent of any programming language. and common API output in wide range of applications.

### &#9780; Overview:
1. [Parsing XML](#-parsing-xml),
2. [Parsing JSON](#-parsing-json),
3. [Generating XML](#-generating-xml),
4. [Generating JSON](#-generating-json),
5. [Key Points](#-key-points)

### &#10022; Parsing XML:
To parse XML documents in PHP with the help of DOM (Document Object Model) using `simplexml_load_string` function. It creates a tree-like structure to represent the XML document and It allows complex manipulations.

  ```php
  $xml = simplexml_load_string('<note><to>Kumar</to><from>Velan</from><heading>Important Message</heading><body>This is greeting from Velan. How are you?</body></note>');

  echo $xml->to;
  echo $xml->from;
  ```

### &#10022; Parsing JSON:
To parse JSON string into array in PHP using `json_decode` function.

```php
$json_string = '{"name":"Kumaran","age":30,"country":"India"}';
$data = json_decode($json_string, true);

echo $data['name'];
echo $data['age'];
```

### &#10022; Generating XML:
Generate XML in PHP using `SimpleXMLElement` class. It Provides a simpler way to access XML data and Suitable for basic XML parsing work.

```php
$xml = new SimpleXMLElement('<note></note>');
$xml->addChild('to', 'Kumar');
$xml->addChild('from', 'Velan');
$xml->addChild('heading', 'Important Message');
$xml->addChild('body', 'This is greeting from Velan. How are you?');

echo $xml->asXML();
```

### &#10022; Generating JSON:
Generate JSON in PHP using `json_encode` function to convert array into JSON string.

```php
$data = array('name' => 'Kumaran', 'age' => 30, 'country' => 'India');
$json_string = json_encode($data);

echo $json_string;
```

### &#10022; Key Points:
- XML: More verbose, hierarchical and DOM based structure, and often used for data exchange between different systems.
- JSON: More concise, easier to parse, and mainly used for data transfer between wide range of applications.
- Performance: JSON is generally faster than XML to parse and generate.

---
[&#8682; To Top](#-xml-and-json)

[&#10094; Previous Topic](./regular-expressions.md) &emsp; [Next Topic &#10095;](./cli-with-php.md)

[&#8962; Goto Home Page](../README.md)