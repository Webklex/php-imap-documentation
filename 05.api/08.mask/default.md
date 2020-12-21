---
title: Mask
---

The package already comes with two default masks [MessageMask::class](https://github.com/Webklex/php-imap/blob/master/src/Support/Masks/MessageMask.php)
and [AttachmentMask::class](https://github.com/Webklex/php-imap/blob/master/src/Support/Masks/AttachmentMask.php).

The masked instance has to be called manually and is designed to add custom functionality.
You can call the default mask by calling the mask method without any arguments.

## Calling a masked instance
There are several methods available to set the default mask:

### 1. Option: set the client default mask

```php
/** @var \Webklex\PHPIMAP\Client $client */
/** @var \Webklex\PHPIMAP\Message $message */
/** @var \Webklex\PHPIMAP\Attachment $attachment */
/** @var \Webklex\PHPIMAP\Support\Masks\MessageMask $message_mask */
/** @var \Webklex\PHPIMAP\Support\Masks\AttachmentMask $attachment_mask */

$message_mask = \Webklex\PHPIMAP\Support\Masks\MessageMask::class;
$attachment_mask = \Webklex\PHPIMAP\Support\Masks\AttachmentMask::class;

$client->setDefaultMessageMask($message_mask);
$client->setDefaultAttachmentMask($attachment_mask);

$message_mask = $message->mask();
$attachment_mask = $attachment->mask();
```

### 2. Option: set the instance default mask

```php
/** @var \Webklex\PHPIMAP\Message $message */
/** @var \Webklex\PHPIMAP\Attachment $attachment */
/** @var \Webklex\PHPIMAP\Support\Masks\MessageMask $message_mask */
/** @var \Webklex\PHPIMAP\Support\Masks\AttachmentMask $attachment_mask */

$message_mask = \Webklex\PHPIMAP\Support\Masks\MessageMask::class;
$attachment_mask = \Webklex\PHPIMAP\Support\Masks\AttachmentMask::class;

$message->setMask($message_mask);
$attachment->setMask($attachment_mask);

$message_mask = $message->mask();
$attachment_mask = $attachment->mask();
```

### 3. Option: apply a temporary mask

```php
/** @var \Webklex\PHPIMAP\Message $message */
/** @var \Webklex\PHPIMAP\Attachment $attachment */
/** @var \Webklex\PHPIMAP\Support\Masks\MessageMask $message_mask */
/** @var \Webklex\PHPIMAP\Support\Masks\AttachmentMask $attachment_mask */

$message_mask = \Webklex\PHPIMAP\Support\Masks\MessageMask::class;
$attachment_mask = \Webklex\PHPIMAP\Support\Masks\AttachmentMask::class;

$message_mask = $message->mask($message_mask);
$attachment_mask = $attachment->mask($attachment_mask);
```

## Create your own mask
Custom message mask example.

```php
class CustomMessageMask extends \Webklex\PHPIMAP\Support\Masks\MessageMask {

    /**
     * New custom method which can be called through a mask
     * @return string
     */
    public function token(){
        return implode('-', [$this->message_id, $this->uid, $this->message_no]);
    }

    /**
     * Get number of message attachments
     * @return integer
     */
    public function getAttachmentCount() {
        return $this->getAttachments()->count();
    }

}
```

Custom attachment mask example.

```php
class CustomAttachmentMask extends \Webklex\PHPIMAP\Support\Masks\AttachmentMask {

    /**
     * New custom method which can be called through a mask
     * @return string
     */
    public function token(){
        return implode('-', [$this->id, $this->getMessage()->getUid(), $this->name]);
    }

    /**
     * Custom attachment saving method
     * @return bool
     */
    public function custom_save() {
        $path = "foo".DIRECTORY_SEPARATOR."bar".DIRECTORY_SEPARATOR;
        $filename = $this->token();

        return file_put_contents($path.$filename, $this->getContent()) !== false;
    }

}
```
