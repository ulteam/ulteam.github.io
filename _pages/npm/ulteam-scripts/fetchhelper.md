---
title: ulteam-scripts FetchHelper
permalink: /npm/ulteam-scripts/fetchhelper/
---

# Class: FetchHelper







Send HTTP requests by fetch



















## Methods




### `Static` sendGetRequest




▸ **sendGetRequest**<**TResponse**>(`pageUrl`: string, `serverRelativeUrl?`: undefined | string): *Promise‹[IWebResponse](interfaces/iwebresponse.md)‹TResponse››*












Send GET request.








**Type parameters:**


▪ TResponse





**Parameters:**





Name | Type | Description |
------ | ------ | ------ |
`pageUrl` | string | Method url |
`serverRelativeUrl?` | undefined \| string | Server relative url  |







**Returns:** *Promise‹[IWebResponse](interfaces/iwebresponse.md)‹TResponse››*








___





### `Static` sendPostRequest




▸ **sendPostRequest**<**TResponse**>(`pageUrl`: string, `serverRelativeUrl?`: undefined | string, `body?`: any): *Promise‹[IWebResponse](interfaces/iwebresponse.md)‹TResponse››*












Send POST request with JSON body.








**Type parameters:**


▪ TResponse





**Parameters:**





Name | Type | Description |
------ | ------ | ------ |
`pageUrl` | string | Method url |
`serverRelativeUrl?` | undefined \| string | Server relative url |
`body?` | any | JSON string  |







**Returns:** *Promise‹[IWebResponse](interfaces/iwebresponse.md)‹TResponse››*














