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
/** @var array $attributes */

$attributes = $message->getAttributes();
```

Example result:

```
array:31 [
  "message_no" => null
  "uid" => 201
  "msgn" => 65
  "msglist" => 0
  "from" => array:1 [
    0 => {#508
      +"personal": "Someone Somewhere"
      +"mailbox": "info"
      +"host": "somehost.com"
      +"mail": "info@somehost.com"
      +"full": "Someone Somewhere <info@somehost.com>"
    }
  ]
  "to" => array:1 [
    0 => {#509
      +"personal": "Someone Somewhere"
      +"mailbox": "test"
      +"host": "somehost.com"
      +"mail": "test@somehost.com"
      +"full": "Someone Somewhere <test@somehost.com>"
    }
  ]
  "cc" => array:2 [
    0 => {#507
      +"personal": "'Someone Somewhere'"
      +"mailbox": "someoneelse"
      +"host": "somehost.com"
      +"mail": "someoneelse@somehost.com"
      +"full": "'Someone Somewhere' <someoneelse@somehost.com>"
    }
    1 => {#506
      +"mailbox": "test"
      +"host": "somehost.com"
      +"personal": false
      +"mail": "test@somehost.com"
      +"full": "test@somehost.com"
    }
  ]
  "reply_to" => array:1 [
    0 => {#505
      +"personal": "Someone Somewhere"
      +"mailbox": "info"
      +"host": "somehost.com"
      +"mail": "info@somehost.com"
      +"full": "Someone Somewhere <info@somehost.com>"
    }
  ]
  "sender" => array:1 [
    0 => {#517
      +"personal": "Someone Somewhere"
      +"mailbox": "info"
      +"host": "somehost.com"
      +"mail": "info@somehost.com"
      +"full": "Someone Somewhere <info@somehost.com>"
    }
  ]
  "subject" => "message subject"
  "message_id" => "3ff121ba-f40e-6df9-cdc2-379aee6b9e36@somehost.com"
  "date" => Carbon\Carbon {#519
    +"date": "2020-12-18 19:18:23.000000"
    +"timezone_type": 1
    +"timezone": "+01:00"
  }
  "return_path" => "<info@somehost.com>"
  "received" => array:16 [
    0 => "from mx1.somehost.com"
    1 => "by localhost with LMTP"
    2 => "id nVpNFHry3F9yTwAA0J78UA"
    3 => "(envelope-from <info@somehost.com>); Fri, 18 Dec 2020 19:18:34 +0100"
    4 => "from localhost (localhost [127.0.0.1])"
    5 => "by mx1.somehost.com (Postfix) with ESMTP id 4AD96140300;"
    6 => "Fri, 18 Dec 2020 19:18:34 +0100 (CET)"
    7 => "from mx1.somehost.com ([127.0.0.1])"
    8 => "by localhost (mx1.somehost.com [127.0.0.1]) (amavisd-new, port 10024)"
    9 => "with ESMTP id zeYHik4AsLTf; Fri, 18 Dec 2020 19:18:24 +0100 (CET)"
    10 => "from [192.168.0.20] (1182014.dynamic.provider.com [11.8.20.14])"
    11 => "(using TLSv1.3 with cipher TLS_AES_128_GCM_SHA256 (128/128 bits)"
    12 => "key-exchange ECDHE (P-256) server-signature RSA-PSS (4096 bits) server-digest SHA256)"
    13 => "(No client certificate requested)"
    14 => "by mx1.somehost.com (Postfix) with ESMTPSA id BD6AD1400C9;"
    15 => "Fri, 18 Dec 2020 19:18:24 +0100 (CET)"
  ]
  "x_virus_scanned" => "Debian amavisd-new at mx1.somehost.com"
  "x_spam_flag" => "NO"
  "x_spam_score" => "-2.9"
  "x_spam_level" => ""
  "x_spam_status" => "No, score=-2.9 required=6.31 tests=[ALL_TRUSTED=-1, BAYES_00=-1.9] autolearn=ham autolearn_force=no"
  "autocrypt" => array:43 [
    0 => "addr=info@somehost.com; keydata="
    1 => "xsFNBFsFVsMBEADlIAbVzjZNkrPfe2E7A8N7GKQjJrxqSpAmQzjmSEwWzhcG9k5LTZmQz7Ct"
    2 => "vK1weOYdQfedsEGMJGOHwr5w4N+jZCDYzga7wiB2X92fLNTCTCJolYsSLQISMT5w0udR+mCZ"
    3 => "jE7WGp2X5yoRPOgqU0gd3xSyrwLXD3/YWZVAoBJ2UoHeMf8NnhX4POzuMQpv+WaxrLNYVfMP"
    4 => "aG8aTnDjgYgkJAM+7c9D5nfTIwXGoxbGGacJww/C8/jIWRPLEbsoadlgIA/E5eI1qCeiz9eg"
    5 => "Qc44mEkSoR22xqpc2QkmJ0Z7rT+KsBE6EwTope59V5detKqLfRPdjWj6R4wFyNDTejaA5Ro2"
    6 => "O3Jk4+StGq/KPpbZNCy0pGvZO8u+9j8FCDXt6JBLI4JERtermFJAYg67anDtvuPpVfuZoyfS"
    7 => "w17l1gFE74nkPsdN1BEu4PFvL9DklJbS8dQAqcDqLCgsIpBJ5me0D8+OydMsknRi+j3KVOXm"
    8 => "bb4KzdX8qtgN/vPKaWZjz3Vq6RaAcnyzxCshjIYMS6lelENO6N0yIcNybSGMs6ogjoThY2ev"
    9 => "O8w6qCz4zqSPbzXwgPnzD3wuvifxJnGuxBWBBuWR+4bYOLvmpCYAIix/ycRHiXmOZKgU1K+w"
    10 => "pOpCovNTfPF8w7iBiHbCOZDdG/UTHFmsbi3v1trmZGMEx6b13QARAQABzSNNYWx0ZSBHb2xk"
    11 => "ZW5iYXVtIDxpbmZvQHdlYmtsZXguY29tPsLBfQQTAQgAJwUCWwVWwwIbIwUJCWYBgAULCQgH"
    12 => "AgYVCAkKCwIEFgIDAQIeAQIXgAAKCRBYw0GBOsa+E8fAD/9y8LNr2O4gII8Y2QK5AmoTOuwh"
    13 => "h+EwTAi9TkTHbcbQRhp6zusjy7VUVeCpxQSv7XKwcgTE6VzBPP3CMLHXPpMdBfev64ksNVKj"
    14 => "cv4jZD66JvOs7FFr2ZUZl3gmPZDStiN9ypqNqM9rA7AnVc1y0ep+cxWSq7JCz7auXii1z/PA"
    15 => "JRwOLYORyWSMR20ClkKtHNMdEa/mefIN+0kSURhsc9Bk6r8yXUpt7SjOW80T/8LVdlbfZoJp"
    16 => "gUry4k/vZZYOrpIR2cfVsdIhPdr/hv1FqsKBUt78o37vZYA5/FnUYlXuM2YEedUvyV6U/NTa"
    17 => "cjVAaYMwbUyBhbPEF1GEWMcoGmSsf0b6aRLfgB01dZNNYnpD4/wpwBfDNjlzkSKbBAZBM4ki"
    18 => "NYZXZVvOni3P1wAH9kYJRtupa1ghjt4P8rA+1CYuYZ3y/tOutsxDrmstngbwnAv1H4NtVqAs"
    19 => "2UOXZovkhE+LrwwgVy1W59sI6NSv1LmjTHGjmsZ5YBDO3XjVMxvzdfgdy9G+UjNHZkwVrQ9O"
    20 => "pzpA9hGdiKtNkdmbWBTiuIland20kdQpxiOp4eyjwMAknfV3eGj65JDQTE2y7OwoVzP2orxg"
    21 => "Vzlbntp1zBCtTDWekRu/dgGdo/SbiECsqzcgZK8ifgMQkPdRzVLi0IHU1GCivRrDXxW1eeNb"
    22 => "UZwX7NoYCs7BTQRbBVbDARAAs0mGzSeGxgdKOeoEMPElvoyDcThW5GCLZL4Zig3weLQ6/JoZ"
    23 => "H53fpak17GZ+MZ4opURtmzKtBCr9ADE5yOfCZgoCrxJGUF6A0r0EP76YcZKBlf9uFhdO7Vpj"
    24 => "pnoPHj+e7ER3G7i5XJc/I07tEXwSCpXgdMBEHQ3FLEXpjlfS0+kXXCgPSWcerJ1pAUzUMyd3"
    25 => "1cBNLavAmruiDk9qZelvuUSOT9E+JkiLyVqm53R/ADqmF1FwMiIVDa6qJoFy12HErFsyyzvh"
    26 => "bY7b9J3tPkWFABA57WMfACMQBFv6LDGaTW+pbbAehDG5INN6cm9VS7T/xUCWAo9GZvQlv70O"
    27 => "yk/OI6X/E5FayX10/u4PNfqYBKf7+AiEaCrIBvbXv/nOJ+/E2DMczBjPIrbWXsNemurtH8gg"
    28 => "Dd0BXT3e/Q1yy4o+YHsVQ6XTDC4uCQvDQwTsVGiesfmgYd0c5Lv41Mfv0Y+lB829tnOOBuxf"
    29 => "vtA0ScPUxF+D0oTfSbwiHsAOOujQq6YEOsghQ3l4WJfhs0mtaPtJSGlTn6dnFN6C1vs1bsRj"
    30 => "EyElbuK8efuBoFMjhQeTgdiHwXsqnRrS5ADIqVCnFlUdCzCOtzr9FbV2MEOaH4nPrYM9Bqzj"
    31 => "QDs++asbZ0juQ/ZFgnbqh2fRXTEoJxxXHZqe0vgD7Ot7wbNXLa8bby7bUc0AEQEAAcLBZQQY"
    32 => "AQgADwUCWwVWwwIbDAUJCWYBgAAKCRBYw0GBOsa+E7w4D/9CncnaZYtTpVsKuFx99YbFKSbP"
    33 => "EgVnE6lGmJhSlOzm2IA++pgk95F4Uw/vUubKmQ3PjEeLkBoPwOp5qF4ojV5cqF4NFGxW3tOn"
    34 => "7awuXW8PKfSFB7dfRMJDPJST1VFhlcQFgaX7lwL9JEczUwbIcI+dSU3+WZ68nYaNWtV1jZSB"
    35 => "x/qXhTZO5Mu0jk6y7yiPpdq87HVLjixCPDiP12pSQXcE8t1kA0KnphzB6MaAzzCWfsaNIUvK"
    36 => "q839593vfmcaho8Wd8sbs0gJyU3BuZwzAoAo0BFkfO56iY+mUV6z9vNcQpKm84Yk0xePec5n"
    37 => "S1wZwN47nhlZ2wSQh58iGbhrrNTS0AN4rUU7z8jSWy2PQGVjpTIX5F11nzCthqHxM6lwyaAE"
    38 => "Jzj+3pOjDnQbaDeavX+Ghnmq1vcMz/IvvkJdjTUm3NmFjebBZeHL6C9J1WJk3/CWFkizcviI"
    39 => "stBSPTpSOGNqZhmPiBnBmQ6vw6tVOiFbg4FqmGZnfGp7uHQV4aXBePRvMdkEe55HM+jDMIso"
    40 => "tbm33JopN/OSRelCTzKAHHjnTc179P7qyJGvvjudFtvnamZjOk5k4YYZ9qnu9wz6LcedUya0"
    41 => "EUxpiq5Gs1JhLA8rTHiI80fQ9euJaSpQgZ/CbbkKJbrlW57wsXdvIPef+vOtgRyNVG0VSl+8"
    42 => "mPkSuHKJvA=="
  ]
  "user_agent" => "Mozilla/5.0 (X11; Linux x86_64; rv:68.0) Gecko/20100101 Thunderbird/68.10.0"
  "mime_version" => "1.0"
  "content_type" => "text/plain"
  "content_transfer_encoding" => "8bit"
  "content_language" => "en-GB"
  "toaddress" => "Someone Somewhere <test@somehost.com>"
  "fromaddress" => "Someone Somewhere <info@somehost.com>"
  "ccaddress" => "'Someone Somewhere' <someoneelse@somehost.com>, test@somehost.com"
  "reply_toaddress" => "Someone Somewhere <info@somehost.com>"
  "senderaddress" => "Someone Somewhere <info@somehost.com>"
  "charset" => "utf-8"
]
```

## Access attributes
There are many possible ways to access specific attributes. Here are some example to access the message subject. The
same can be done to any other attribute you can find in `Message::getAttributes()`.

```php
/** @var \Webklex\PHPIMAP\Message $message */
/** @var string $subject */

$subject = $message->subject;
$subject = $message->getSubject();
$subject = $message->get("subject");
$subject = $message->getAttributes()["subject"];
```
