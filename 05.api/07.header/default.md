---
title: Header
---

## Access attributes
There are many possible ways to access specific attributes. Here are some example to access an attribute called "subject".
The same can be done to any other attribute you can find in `Header::getAttributes()`.

```php
/** @var \Webklex\PHPIMAP\Header $header */
/** @var string $subject */

$subject = $header->subject;
$subject = $header->getSubject();
$subject = $header->get("subject");
$subject = $header->getAttributes()["subject"];
```


## Find attribute
You can apply a regex on the raw header to search for any value / key you want.

```php
/** @var \Webklex\PHPIMAP\Header $header */
/** @var string $boundary */

$boundary = $header->find("/boundary=\"?([^\"]*)[\";\s]/");
```
