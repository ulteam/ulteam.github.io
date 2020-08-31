---
title: ulteam-scripts FetchHelper
permalink: /npm/ulteam-scripts/fetchhelper/
---

## FetchHelper class

Send HTTP requests by fetch API




#### Methods

| Name | Returns | Static | Description |
|-|-|-|-|
| sendGetRequest\<TResponse\>(pageUrl: string, serverRelativeUrl: undefined &#124; string) | Promise\<IWebResponse\<TResponse\>\> |  `Static`  | Send GET request.  <br> **pageUrl**: *Method url*  <br> **serverRelativeUrl**: *Server relative url <br>*  |
| sendPostRequest\<TResponse\>(pageUrl: string, serverRelativeUrl: undefined &#124; string, body: any) | Promise\<IWebResponse\<TResponse\>\> |  `Static`  | Send POST request with JSON body.  <br> **pageUrl**: *Method url*  <br> **serverRelativeUrl**: *Server relative url*  <br> **body**: *JSON string <br>*  |
