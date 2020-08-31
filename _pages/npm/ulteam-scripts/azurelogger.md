---
title: ulteam-scripts AzureLogger
permalink: /npm/ulteam-scripts/azurelogger/
---

## AzureLogger class

Work with Azure Application Insights

### Sample

```tsx
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

#### Constructors

| Name | Description |
|-|-|
| new AzureLogger(instrumentationKey: string, authenticatedUserId: string, projectName: string, commonProperties: undefined &#124; { [key: string]: any }) | Set configuration  <br> **instrumentationKey**: *Azure Application Insight App instrumentation key*  <br> **authenticatedUserId**: *The authenticated user id. A unique and persistent string that represents each authenticated user in the service. <br>It should not contain commas, semi-colons, equal signs, spaces, or vertical-bars <br>If userEmail is not undefined then Sets the autheticated user id and the account id in this session (setAuthenticatedUserContext API method).*  <br> **projectName**: *Your project name. Name should be contain only english letters and 'dot' char. For example: 'SampleCompany'*  <br> **commonProperties**: *There are properties associated to all events, like ListItem.Id. This properties will be added to Event Custom Properties. <br>*  |

#### Properties

| Name | Static | Description |
|-|-|-|
| authenticatedUserId: string |  | The authenticated user id. A unique and persistent string that represents each authenticated user in the service. |
| commonProperties: { [key: string]: any } |  | There are properties associated to all events. |
| context: ApplicationInsights |  | Context of Application Insights. |
| projectName: string |  | Your project name. |

#### Methods

| Name | Returns | Static | Description |
|-|-|-|-|
| init(addPageTracking: undefined &#124; false &#124; true, pageTrackingFilter: string[]) | void |  | Download full Application Insights script from CDN and initialize it with instrumentation key.  <br> **addPageTracking**: *Activate page tracking by calling trackPageView method. Default value is true.*  <br> **pageTrackingFilter**: *Filter your Network by parts of url. <br>If url has one of this filters then it will be added to Application Insights Remote Dependencies <br>*  |
| trackEvent(eventName: string, properties: undefined &#124; { [key: string]: any }) | void |  | Add custom event (log line). <br>In Azure Application Insights App search this event by this template: '{projectName}.JS.{eventName}'.  <br> **eventName**: *Custom event name. <br>It should contains only english letters without spaces.*  <br> **properties**: *There are properties associated only to this event. This properties will be added to Event Custom Properties. <br>*  |
| trackException(exception: Error, properties: undefined &#124; { [key: string]: any }) | void |  | Add exception. <br>In Azure Application Insights App search this event by this template: '{projectName}.JS.Exception'.  <br> **exception**: *JS/TS exception.*  <br> **properties**: *There are properties associated only to this event. This properties will be added to Event Custom Properties. <br>*  |
| trackPageView(pageTrackingFilter: string[], properties: undefined &#124; { [key: string]: any }) | void |  | Logs user session info about browser, network requests, etc. <br>In Azure Application Insights App search this event by this template: '{projectName}.JS.PageView'.  <br> **pageTrackingFilter**: *Filter your Network by parts of url. <br>If url has one of this filters then it will be added to Application Insights Remote Dependencies*  <br> **properties**: *There are properties associated only to this event. This properties will be added to Event Custom Properties. <br>*  |
