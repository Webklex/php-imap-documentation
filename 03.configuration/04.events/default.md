---
menu: Events
title: Event Configuration
---
Events get called throughout the entire package and allow you to automate certain actions.


## Message events

**Available events:**<br />
`new`  &mdash; A new message has been created<br />
`moved`  &mdash; A message has been moved<br />
`copied`  &mdash; A message has been copied<br />
`deleted`  &mdash; A message has been deleted<br />
`restored`  &mdash; A message has been restored<br />

```text
Property: message
Value:    array
```


## Folder events

**Available events:**<br />
`new`  &mdash; A new folder has been created<br />
`moved`  &mdash; A folder has been moved<br />
`deleted`  &mdash; A folder has been deleted<br />

```text
Property: folder
Value:    array
```


## Flag events

**Available events:**<br />
`new`  &mdash; A flag has been added<br />
`deleted`  &mdash; A flag has been removed<br />

```text
Property: flag
Value:    array
```
