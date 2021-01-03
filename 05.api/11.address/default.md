---
title: Address
---

Attributes are a flexible class made to handle any message attributes as either a string or array.

## Get String
To receive the string value of the current address:
```php
/** @var \Webklex\PHPIMAP\Address $address */

$value = "$address";
$value = (string)$address;
$value = $address->toString();
$value = $address->__toString();
```

## Get Array
To receive the array values of the current attribute:
```php
/** @var \Webklex\PHPIMAP\Address $address */

foreach($address as $key => $value) {
    echo $value."\n";
}
$values = (array)$address;
$values = $address->toArray();
$values = $address->__serialize();
```

## Structure of an Address
```text
Webklex\PHPIMAP\Address {#505
  +personal: "Some One"
  +mailbox: "example"
  +host: "somehost.com"
  +mail: "example@somehost.com"
  +full: "Some One <example@somehost.com>"
}
```


