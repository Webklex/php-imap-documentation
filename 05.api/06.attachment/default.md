---
title: Attachment
---


## Save attachment
Save the attachment content to a specific location. The attachment name is used as filename if none is provided.

```php
/** @var \Webklex\PHPIMAP\Attachment $attachment */
/** @var boolean $status */

$status = $attachment->save($path = "./some/location/", $filename = null);
```

## Get mime type
Try to identify the attachment mime type.

```php
/** @var \Webklex\PHPIMAP\Attachment $attachment */
/** @var string|null $mime */

$mime = $attachment->getMimeType();
```

## Get extension
Try to identify the attachment extension.

```php
/** @var \Webklex\PHPIMAP\Attachment $attachment */
/** @var string|null $ext */

$ext = $attachment->getExtension();
```


## Get all attributes
Receive a list of all available attributes. These include also all parsed [Header](../header) attributes.

```php
/** @var \Webklex\PHPIMAP\Attachment $attachment */
/** @var array $attributes */

$attributes = $attachment->getAttributes();
```

Example result:
```
array:9 [
  "content" => "some sample text\n"
  "type" => "text"
  "part_number" => 2
  "content_type" => "text/plain"
  "id" => null
  "name" => "test.txt"
  "disposition" => "attachment"
  "img_src" => null
  "size" => 24
]
```


## Access attributes
There are many possible ways to access specific attributes. Here are some example to access the attachment name. The
same can be done to any other attribute you can find in `Message::getAttributes()`.

```php
/** @var \Webklex\PHPIMAP\Attachment $attachment */
/** @var string $name */

$name = $attachment->name;
$name = $attachment->getName();
$name = $attachment->get("name");
$name = $attachment->getAttributes()["name"];
```
