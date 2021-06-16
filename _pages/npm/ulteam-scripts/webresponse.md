---
title: ulteam-scripts WebResponse
permalink: /npm/ulteam-scripts/webresponse/
---

## WebResponse class

Work with the Response object of the fetch API.




#### Methods

| Name | Returns | Static | Description |
|-|-|-|-|
| get\<TData\>(response: Response) | Promise\<IWebResponse\<TData\>\> |  `Static`  | Parse response payload and return IWebResponse object as a result.  <br> **response**: *Fetch API response <br>*  |
| getDefault\<TData\>(type: WebResponseDefaultType, data: TData) | IWebResponse\<TData\> |  `Static`  | Get IWebResponse object based on response type and data object.  <br> **type**: *IWebResponse type*  <br> **data**: *Payload data <br>*  |
