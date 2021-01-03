---
title: Attribute
---

Attributes are a flexible class made to handle any message attributes as either a string or array.

## Get String
To receive the string value of the current attribute:
```php
/** @var \Webklex\PHPIMAP\Attribute $attribute */

$value = "$attribute";
$value = (string)$attribute;
$value = $attribute->toString();
$value = $attribute->__toString();
```

## Get Array
To receive the array values of the current attribute:
```php
/** @var \Webklex\PHPIMAP\Attribute $attribute */

foreach($attribute as $key => $value) {
    echo $value."\n";
}
$values = (array)$attribute;
$values = $attribute->toArray();
$values = $attribute->__serialize();
```

## Check if value is contained
Check if the current attribute contains a given value:
```php
/** @var \Webklex\PHPIMAP\Attribute $attribute */

$check = $attribute->contains($value = "fooBar");
```

## Attach value
Attach a new value to the attribute. If you want to make shure the value is unique, set `$strict` to true.
```php
/** @var \Webklex\PHPIMAP\Attribute $attribute */

$attribute->attach($value = "fooBar", $strict = false);
```

## Get first
Get the first element of the attribute values:
```php
/** @var \Webklex\PHPIMAP\Attribute $attribute */

$value = $attribute->first();
```

## Get last
Get the last element of the attribute values:
```php
/** @var \Webklex\PHPIMAP\Attribute $attribute */

$value = $attribute->last();
```

## Structure of an Attribute
This is the example structure of a subject:
```text
Webklex\PHPIMAP\Attribute {#527
  #name: "subject"
  #values: array:1 [
    0 => "Some subject"
  ]
}
```
