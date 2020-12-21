---
menu: Advanced
title: Advanced Configuration
---


## Folder / Mailbox delimiter
You can use any supported char such as ".", "/", (...).
```text
Property: delimiter
Value:    anything
```

## Fetching method
If set to `FT_PEEK` all unread messages are left as such. If set to `FT_UID` all parsed unread messages will be flagged as
seen.
```text
Property: fetch
Value:    IMAP::FT_PEEK or IMAP::FT_UID
```

## Communication sequence type
If the sequence is set to `ST_MSGN` the communication is based on the message number. If set to `ST_UID` the communication
is based the the uid.
```text
Property: sequence
Value:    IMAP::ST_MSGN or IMAP::ST_UID
```

## Fetch message bodies
Enable this option if the message body should always be downloaded. Disabling this can greatly increase the overall
performance.
```text
Property: fetch_body
Value:    true or false
```

## Fetch message flags
Enable this option if the message flags should always be downloaded. Only takes affect if `fetch` is not set to `FT_PEEK`.
```text
Property: fetch_flags
Value:    true or false
```

## Message key identifier
You can choose between these different options:

`id`     &mdash; Use the MessageID as array key (default, might cause hickups with yahoo mail) <br />
`number` &mdash; Use the message number as array key (isn't always unique and can cause some interesting behavior) <br />
`list`   &mdash; Use the message list number as array key (incrementing integer (does not always start at 0 or 1) <br />
`uid`    &mdash; Use the message uid as array key (isn't always unique and can cause some interesting behavior) <br />

```text
Property: message_key
Value:    any of the above
```

## Message fetch order
You can choose between these two different options:

`asc`  &mdash; Order all messages ascending (probably results in oldest first)<br />
`desc` &mdash; Order all messages descending (probably results in newest first)<br />

```text
Property: fetch_order
Value:    any of the above
```

## Message disposition types
Disposition types potentially considered an attachment.
```text
Property: dispositions
Value:    array of supported disposition types
```

## Common folders
An associated array containing common folder names and their paths.

`root`  &mdash; Inbox folder<br />
`junk`  &mdash; Junk or spam folder<br />
`draft` &mdash; Draft messages folder<br />
`sent`  &mdash; Sent messages folder<br />
`trash` &mdash; Trashed or deleted messages folder<br />

```text
Property: common_folders
Value:    array
```

## Message & Attachment decoding

**Properties:**<br />
`message`  &mdash; Inbox folder<br />
`attachment`  &mdash; Junk or spam folder<br />

**Value:**<br />
`utf-8`  &mdash; Try decoding based on utf-8<br />
`mimeheader`  &mdash; Try decoding using the `mbstring` module<br />

```text
Property: decoder
Value:    array
```

## Legacy imap open options
If you are using a legacy protocol you can provide additional options to the native php `imap_open()` method.

`DISABLE_AUTHENTICATOR` &mdash; Disable authentication properties

```text
Property: open
Value:    array
```
