---
title: ulteam-scripts Helper
permalink: /npm/ulteam-scripts/helper/
---

## Helper class

Set of common / helper functions




#### Methods

| Name | Returns | Static | Description |
|-|-|-|-|
| getParameterByName(parameterName: string, url: undefined &#124; string) | string |  `Static`  | Get URL parameter value  <br> **parameterName**: *URL parameter name*  <br> **url**: *Set your URL except location.search if needed <br>*  |
| waitElementLoad(selector: string, waitingTime: number, maxWaitingTime: number) | Promise\<HTMLElement &#124; null\> |  `Static`  | Wait until the DOM element will be loaded  <br> **selector**: *DOM selector*  <br> **waitingTime**: *Waiting time before the next attemp (in milliseconds). Default is 100 ms*  <br> **maxWaitingTime**: *Max waiting time in milliseconds. If element will not be finded then returns null. Default is 10 000 ms <br>*  |
