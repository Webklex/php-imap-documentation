---
title: Query
---

## Get a specific message
Based on your configuration you can either receive a specific message by providing a message number (if your fetch
option is set to ST_MSGN) or providing a uid.

```php
/** @var \Webklex\PHPIMAP\Query\WhereQuery $query */
/** @var \Webklex\PHPIMAP\Message $message */

$message = $query->getMessage($id = 1);
```


## Get all messages
Get a collection of all available messages.

```php
/** @var \Webklex\PHPIMAP\Query\WhereQuery $query */
/** @var \Webklex\PHPIMAP\Support\MessageCollection $messages */

$messages = $query->all()->get();
```


## Flag all fetched messages as read
You can automatically flag all fetched messages as "seen".

```php
/** @var \Webklex\PHPIMAP\Query\WhereQuery $query */

$query->markAsRead();
```


## Don't flag all fetched messages as read
You can prevent the server from automatically flagging all fetched messages as "seen".

```php
/** @var \Webklex\PHPIMAP\Query\WhereQuery $query */

$query->leaveUnread();
```


## Don't fetch the message body
If your script takes for ever to complete, or if you don't need the body, you can prevent the body fetching.

```php
/** @var \Webklex\PHPIMAP\Query\WhereQuery $query */

$query->setFetchBody(false);
```


## Limit the result
Limit the result to a specific limit and / or page. This has a great positive effect on your execution time.

```php
/** @var \Webklex\PHPIMAP\Query\WhereQuery $query */
/** @var \Webklex\PHPIMAP\Support\MessageCollection $messages */

$messages = $query->all()->limit($limit = 10, $page = 2)->get();
```


## Count the result
Count the amount of available messages without fetching them.

```php
/** @var \Webklex\PHPIMAP\Query\WhereQuery $query */
/** @var integer $count */

$count = $query->all()->count();
```

## Get a paginated result
Get a paginated collection of all available messages. Here is a [pagination example](../../examples/pagination).

```php
/** @var \Webklex\PHPIMAP\Query\WhereQuery $query */
/** @var \Illuminate\Pagination\LengthAwarePaginator $paginator */

$paginator = $query->all()->paginate($per_page = 5, $page = null, $page_name = 'imap_page');
```


## Set the sort order
You can define the way the fetched messages should be ordered. Use "asc" for ascending and "desc" to order descending.

```php
/** @var \Webklex\PHPIMAP\Query\WhereQuery $query */
/** @var integer $count */

$query->setFetchOrder("asc");
$query->setFetchOrderAsc();
$query->fetchOrderAsc();

$query->setFetchOrder("desc");
$query->setFetchOrderDesc();
$query->fetchOrderDesc();
```


## Get all messages from a specific sender
Get a collection of all available messages from a specific sender. In this case "example@domain.com".

```php
/** @var \Webklex\PHPIMAP\Query\WhereQuery $query */
/** @var \Webklex\PHPIMAP\Support\MessageCollection $messages */

$messages = $query->from('example@domain.com')->get();
```

## Get all messages since a specific date
Get a collection of all available messages which were sent after after a given date. The IMAP protocol does not allow to
search for datetime keywords.

```php
/** @var \Webklex\PHPIMAP\Query\WhereQuery $query */
/** @var \Webklex\PHPIMAP\Support\MessageCollection $messages */

$messages = $query->since('15.03.2018')->get();
$messages = $query->since(\Carbon\Carbon::now()->subDays(5))->get();
```

## Get all messages containing a specific text
Get a collection of all available messages containing a specific text.

```php
/** @var \Webklex\PHPIMAP\Query\WhereQuery $query */
/** @var \Webklex\PHPIMAP\Support\MessageCollection $messages */

$messages = $query->text('hello world')->get();
```


## Alternative method names
Every search criteria can be added using several different naming schemes. Here is an example for `Query::text()`.

```php
/** @var \Webklex\PHPIMAP\Query\WhereQuery $query */
/** @var \Webklex\PHPIMAP\Support\MessageCollection $messages */

$messages = $query->text('hello world')->get();
$messages = $query->Text('hello world')->get();
$messages = $query->whereText('hello world')->get();
$messages = $query->where([['TEXT', 'Hello world']])->get();
```


## Search by excluding
You can also search for messages which do not match the criteria. Like a negative search criteria.
In this example, all messages which do not contain the text "hello world".

```php
/** @var \Webklex\PHPIMAP\Query\WhereQuery $query */
/** @var \Webklex\PHPIMAP\Support\MessageCollection $messages */

$messages = $query->notText('hello world')->get();
$messages = $query->not_text('hello world')->get();
$messages = $query->not()->text('hello world')->get();
```


## Chained search criteria
You might want to search for all messages from a certain sender, which are also unseen and have to contain a specific text.

```php
/** @var \Webklex\PHPIMAP\Query\WhereQuery $query */
/** @var \Webklex\PHPIMAP\Support\MessageCollection $messages */

$messages = $query->from('example@domain.com')->unseen()->text('hello world')->get();
```


## Custom search criteria
Your provider supports custom search criteria? Great! Here is an example where the criteria "FOOBAR" is available and
consumes a string.

```php
/** @var \Webklex\PHPIMAP\Query\WhereQuery $query */
/** @var \Webklex\PHPIMAP\Support\MessageCollection $messages */

$messages = $query->where([["CUSTOM_FOOBAR" => "fooBar"]])->get();
```


## All available search criteria
- `ALL` — return all messages matching the rest of the criteria
- `ANSWERED` — match messages with the \ANSWERED flag set
- `BCC` "string" — match messages with "string" in the Bcc: field
- `BEFORE` "date" — match messages with Date: before "date"
- `BODY` "string" — match messages with "string" in the body of the message
- `CC` "string" — match messages with "string" in the Cc: field
- `DELETED` — match deleted messages
- `FLAGGED` — match messages with the \FLAGGED (sometimes referred to as Important or Urgent) flag set
- `FROM` "string" — match messages with "string" in the From: field
- `KEYWORD` "string" — match messages with "string" as a keyword
- `NEW` — match new messages
- `NOT` — not matching
- `OLD` — match old messages
- `ON` "date" — match messages with Date: matching "date"
- `RECENT` — match messages with the \RECENT flag set
- `SEEN` — match messages that have been read (the \SEEN flag is set)
- `SINCE` "date" — match messages with Date: after "date"
- `SUBJECT` "string" — match messages with "string" in the Subject:
- `TEXT` "string" — match messages with text "string"
- `TO` "string" — match messages with "string" in the To:
- `UNANSWERED` — match messages that have not been answered
- `UNDELETED` — match messages that are not deleted
- `UNFLAGGED` — match messages that are not flagged
- `UNKEYWORD` "string" — match messages that do not have the keyword "string"
- `UNSEEN` — match messages which have not been read yet
