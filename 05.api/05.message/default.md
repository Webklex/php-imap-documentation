---
title: Message
---

## Check if a text body exists

```php
/** @var \Webklex\PHPIMAP\Message $message */
/** @var boolean $status */

$status = $message->hasTextBody();
```

## Check if an html body exists

```php
/** @var \Webklex\PHPIMAP\Message $message */
/** @var boolean $status */

$status = $message->hasHTMLBody();
```

## Get text body
Get the parsed message text body. Will return null if none is present.

```php
/** @var \Webklex\PHPIMAP\Message $message */
/** @var string|null $body */

$body = $message->getTextBody();
```

## Get html body
Get the parsed message text body. Will return null if none is present.

```php
/** @var \Webklex\PHPIMAP\Message $message */
/** @var string|null $body */

$body = $message->getHTMLBody();
```

## Get bodies
Get both parsed message text and html bodies.

```php
/** @var \Webklex\PHPIMAP\Message $message */
/** @var array $bodies */

$bodies = $message->getBodies();
```

## Fetch body
Fetch the message body. This method can be used to load / fetch the message body if the body fetching has been disabled
previously.

```php
/** @var \Webklex\PHPIMAP\Message $message */

$message->parseBody();
```

## Get the containing folder
Get a folder instance based on the folder the message is located in.

```php
/** @var \Webklex\PHPIMAP\Message $message */
/** @var \Webklex\PHPIMAP\Folder $folder */

$folder = $message->getFolder();
```

## Message thread
Get the message thread by comparing the `message_id` and `in_reply_to` headers of both the current message and all
messages in your sent messages folder. This action is recursive and might take a few seconds to locate all connected
messages.

```php
/** @var \Webklex\PHPIMAP\Message $message */
/** @var \Webklex\PHPIMAP\Support\MessageCollection $messages */

$messages = $message->thread($sent_folder = null);
```

## Copy message
Copy the current message into a different folder. Based on your mail provider, you might not get the moved message as
back as response. In this case null is returned.

```php
/** @var \Webklex\PHPIMAP\Message $message */
/** @var \Webklex\PHPIMAP\Message $copy */

$copy = $message->copy($folder_path = "INBOX.name");
```

## Move message
Move the current message into a different folder. Based on your mail provider, you might not get the moved message as
back as response. In this case null is returned.

```php
/** @var \Webklex\PHPIMAP\Message $message */

$message = $message->move($folder_path = "INBOX.name");
```

## Delete message
Delete the current message. This action won't complete if $expunge is set to false, until the connection gets expunged.

```php
/** @var \Webklex\PHPIMAP\Message $message */

$message = $message->delete($expunge = true);
```

## Restore message
Restore the current message. This action won't complete if $expunge is set to false, until the connection gets expunged.

```php
/** @var \Webklex\PHPIMAP\Message $message */

$message = $message->restore($expunge = true);
```

## Get flags
Get all parsed message flags.

```php
/** @var \Webklex\PHPIMAP\Message $message */
/** @var \Webklex\PHPIMAP\Support\FlagCollection $flags */

$flags = $message->getFlags();
```

## Add a new flag
You can add several new flags at once or just a single one.

```php
/** @var \Webklex\PHPIMAP\Message $message */

$message->setFlag(['Seen', 'Flagged']);
$message->setFlag('Seen');
```

## Remove a flag
Remove an existing message flag from the current message.

```php
/** @var \Webklex\PHPIMAP\Message $message */

$message->unsetFlag('Flagged');
```

## Check if the message has attachments
Check if the current message has any attachments.

```php
/** @var \Webklex\PHPIMAP\Message $message */
/** @var boolean $status */

$status = $message->hasAttachments();
```

## Get all attachments
Receive a collection of all attached files.

```php
/** @var \Webklex\PHPIMAP\Message $message */
/** @var \Webklex\PHPIMAP\Support\AttachmentCollection $attachments */

$attachments = $message->getAttachments();
```

## Get raw body
Receive the raw and unparsed message body.

```php
/** @var \Webklex\PHPIMAP\Message $message */
/** @var string $raw */

$raw = $message->getRawBody();
```

## Get header
Receive the parsed [Header](../header) instance.

```php
/** @var \Webklex\PHPIMAP\Message $message */
/** @var \Webklex\PHPIMAP\Header $header */

$header = $message->getHeader();
```

## Get all attributes
Receive a list of all available attributes. These include also all parsed [Header](../header) attributes.

```php
/** @var \Webklex\PHPIMAP\Message $message */
/** @var \Webklex\PHPIMAP\Attribute[]  $attributes */

$attributes = $message->getAttributes();
```

## Access attributes
There are many possible ways to access specific attributes. Here are some example to access the message subject. The
same can be done to any other attribute you can find in `Message::getAttributes()`.

```php
/** @var \Webklex\PHPIMAP\Message $message */
/** @var \Webklex\PHPIMAP\Attribute $subject */

$subject = $message->subject;
$subject = $message->getSubject();
$subject = $message->get("subject");
$subject = $message->getAttributes()["subject"];
```

Check out the [Attribute](../attribute) section to learn more about the attribute handling and available magic methods.
