---
title: ulteam-scripts ULogger
permalink: /npm/ulteam-scripts/ulogger/
---

## ULogger class

Class for logging messages & errors to DOM and console.

### Sample

```tsx
import { ULogger } from "../../log/ULogger";

export class TestULogger {
  public static Sample() {
    const container = document.querySelector('.ms-formtable');

    // log info text
    ULogger.info(container, "Sample info text");

    // log error in catch block
    try {
      throw new Error("Sample error");
    }
    catch (e) {
      ULogger.error(container, e);
    }
  }
}
```



#### Methods

| Name | Returns | Static | Description |
|-|-|-|-|
| error(container: Element &#124; HTMLElement &#124; null, e: Error, message: undefined &#124; string) | void |  `Static`  | Log error message  <br> **container**: *Add log to this element as a first child element*  <br> **e**: *JS Error object*  <br> **message**: *Additional info <br>*  |
| info(container: Element &#124; HTMLElement &#124; null, message: string) | void |  `Static`  | Log message or debug info  <br> **container**: *Add log to this element as a first child element*  <br> **message**: *Log text <br>*  |
