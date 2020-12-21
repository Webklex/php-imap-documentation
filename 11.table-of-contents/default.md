---
title: Table of Contents
---

1. [Documentation](../)
1. [Installation](../installation)
    1. Install php dependencies
    1. Option 1: Install with composer
    1. Option 2: Install from GitHub
    1. Legacy support
1. Configuration
    1. [Base Configuration](../configuration/configuration)
        1. Default date format
        1. Default account
        1. Available accounts
        1. Advanced fetching configuration
        1. Event configuration
        1. Mask configuration
    1. [Account Configuration](../configuration/account/account)
        1. Host
        1. Port
        1. Protocol
        1. Encryption method
        1. Certificate validation
        1. Username
        1. Password
        1. Authentication method
        1. Proxy
    1. [Proxy Configuration](../configuration/account/proxy)
        1. Socket
        1. Request full uri
        1. Username
        1. Password
    1. [Advanced Configuration](../configuration/advanced)
        1. Folder / Mailbox delimiter
        1. Fetching method
        1. Communication sequence type
        1. Fetch message bodies
        1. Fetch message flags
        1. Message key identifier
        1. Message fetch order
        1. Message disposition types
        1. Common folders
        1. Message & Attachment decoding
        1. Legacy imap open options
    1. [Event Configuration](../configuration/events)
        1. Message events
        1. Folder events
        1. Flag events
    1. [Mask Configuration](../configuration/masks)
        1. Message mask
        1. Attachment mask
1. Examples
    1. [Getting started](../examples/getting-started)
    1. [oAuth using Google](../examples/oauth)
        1. Connect using an application password
    1. [Message pagination](../examples/pagination)
    1. [Proxy](../examples/proxy)
1. Api
    1. [ClientManager](../api/client-manager)
        1. New instance from config file
        1. New instance from array
        1. New preconfigured account
        1. Make a new client
        1. Get a specific config value
    1. [Client](../api/client)
        1. Connect to the server
        1. Get the connection status
        1. Check the current connection
        1. Force reconnect
        1. Close connection
        1. List all available folders
        1. Find a folder by path
        1. Find a folder by name
        1. Find a folder by name or path
        1. Create new folder
        1. Get folder detail
    1. [Folder](../api/folder)
        1. New search query
        1. Check if the folder has sub folder
        1. Move a folder
        1. Delete a folder
        1. Idle connection
        1. Get folder detail
        1. Folder overview
    1. [Query](../api/query)
        1. Get a specific message
        1. Get all messages
        1. Flag all fetched messages as read
        1. Don't flag all fetched messages as read
        1. Don't fetch the message body
        1. Limit the result
        1. Count the result
        1. Get a paginated result
        1. Set the sort order
        1. Get all messages from a specific sender
        1. Get all messages since a specific date
        1. Get all messages containing a specific text
        1. Alternative method names
        1. Search by excluding
        1. Chained search criteria
        1. Custom search criteria
        1. All available search criteria
    1. [Message](../api/message)
        1. Check if a text body exists
        1. Check if an html body exists
        1. Get text body
        1. Get html body
        1. Get bodies
        1. Fetch body
        1. Get the containing folder
        1. Message thread
        1. Copy message
        1. Move message
        1. Delete message
        1. Restore message
        1. Get flags
        1. Add a new flag
        1. Remove a flag
        1. Check if the message has attachments
        1. Get all attachments
        1. Get raw body
        1. Get header
        1. Get all attributes
        1. Access attributes
    1. [Attachment](../api/attachment)
        1. Save attachment
        1. Get mime type
        1. Get extension
        1. Get all attributes
        1. Access attributes
    1. [Header](../api/header)
        1. Access attributes
        1. Find attribute
    1. [Mask](../api/mask)
        1. Calling a masked instance
        1. Create your own mask
    1. [Event](../api/event)
        1. Available events
        1. Custom event
1. Frameworks
    1. Laravel
        1. [Installation](../frameworks/laravel/installation)
            1. Install php dependencies
            1. Install with composer
            1. Legacy support
            1. Older Laravel versions < 5.5
            1. Publish the configuration file
        1. [Configuration](../frameworks/laravel/configuration)
        1. [Facade](../frameworks/laravel/facade)
        1. [Events](../frameworks/laravel/events)
        1. [Commands](../frameworks/laravel/commands)
            1. Event driven
            1. Custom Command
        1. [Service setup](../frameworks/laravel/service)
1. [Support](../support)
    1. Features & pull requests
    1. A little notice
1. [Security](../security)
1. [About](../about)
1. [Donate](../donate)
