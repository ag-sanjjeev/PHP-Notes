## &#10162; XML and JSON:
XML and JSON are file formats that used to store and exchange data as per requirements.
XML stands for Extensible Markup Language. XML supports information exchange between computer systems.
JSON stands for JavaScript Object Notation. JSON is independent of any programming language. and common API output in wide range of applications.

### &#9780; Overview:
1. [Parsing XML](#-parsing-xml)
2. [Parsing JSON](#-parsing-json)
3. [Generating XML](#-generating-xml)
4. [Generating JSON](#-generating-json)
5. [Key Points](#-key-points)

### &#10022; Parsing XML:
To parse XML documents in PHP with the help of DOM (Document Object Model) using `simplexml_load_string` function. It creates a tree-like structure to represent the XML document and It allows complex manipulations.

```php
$xmlstring = '<note><to>Kumar</to><from>Velan</from><heading>Important Message</heading><body>This is greeting from Velan. How are you?</body></note>';
$xml = simplexml_load_string($xmlstring);

echo $xml->to;
echo $xml->from;
```

- Using `DOMDocument`, It is more powerful for complex XML structures.and It allows to manipulate the XML document as a tree structure.

```php
$xmlstring = '<note><to>Kumar</to><from>Velan</from><heading>Important Message</heading><body>This is greeting from Velan. How are you?</body></note>';
$doc = new DOMDocument();
$doc->loadXML($xmlstring);

$to = $doc->getElementsByTagName('to')->item(0)->nodeValue;
echo $to;
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

- Using `DOMDocument` to create XML in PHP.

```php
$doc = new DOMDocument();
$doc->formatOutput = true;

$root = $doc->createElement('note');
$doc->appendChild($root);

$to = $doc->createElement('to');
$to->appendChild($doc->createTextNode('Kumar'));
$root->appendChild($to);

$from = $doc->createElement('from');
$from->appendChild($doc->createTextNode('Velan'));
$root->appendChild($from);

$heading = $doc->createElement('heading');
$heading->appendChild($doc->createTextNode('Important Message'));
$root->appendChild($heading);

$body = $doc->createElement('body');
$body->appendChild($doc->createTextNode('This is greeting from Velan. How are you?'));
$root->appendChild($body);

echo $doc->saveXML();
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

[&#10094; Previous Topic](./cryptographic-functionalities.md) &emsp; [Next Topic &#10095;](./cli-with-php.md)

[&#8962; Goto Home Page](../README.md)