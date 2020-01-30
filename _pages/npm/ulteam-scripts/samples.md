---
title: ulteam-scripts samples
permalink: /npm/ulteam-scripts/samples/
---

## Sample 1

```js
import { AzureLogger } from "../../log/AzureLogger";


export class TestAzureLogger {
  public static Test() {

    /** create logger instance */
    const logger: AzureLogger = new AzureLogger(
      /** Application Insights instrumentation key */
      "c7310ee5-8c8f-4c26-87b5-f166c9c4e8a8",
      /** user authentification id */
      "user@sample.com",
      /** project name */
      "ulteam.scripts",
      /** main list item id */
      { itemId: 123 }
    );

    const pageTrackingFilters = [ "localhost" ];

    /** Initialize Application Insights scripts */
    logger.init(true, pageTrackingFilters);
    /** type logger.init(false) if you don't need tracking Page View */

    /** add custom event */
    logger.trackEvent("Start.TestAzureLogger"); 

    try {
      /** exception example */
      throw new Error("JavaScript error message");
    }
    catch (e) {
      logger.trackException(e);
    }

    /** add custom event */
    logger.trackEvent("Finish");
  }
}
```