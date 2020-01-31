---
title: ulteam-scripts AzureLogger
permalink: /npm/ulteam-scripts/azurelogger/
---


# Class: AzureLogger







Work with Azure Application Insights



















## Constructors




###  constructor




\+ **new AzureLogger**(`instrumentationKey`: string, `authenticatedUserId`: string, `projectName`: string, `commonProperties?`: undefined | object): *[AzureLogger](classes/azurelogger.md)*












Set configuration









**Parameters:**





Name | Type | Description |
------ | ------ | ------ |
`instrumentationKey` | string | Azure Application Insight App instrumentation key |
`authenticatedUserId` | string | The authenticated user id. A unique and persistent string that represents each authenticated user in the service. It should not contain commas, semi-colons, equal signs, spaces, or vertical-bars If userEmail is not undefined then Sets the autheticated user id and the account id in this session (setAuthenticatedUserContext API method). |
`projectName` | string | Your project name. Name should be contain only english letters and 'dot' char. For example: 'SampleCompany' |
`commonProperties?` | undefined \| object | There are properties associated to all events, like ListItem.Id. This properties will be added to Event Custom Properties.  |







**Returns:** *[AzureLogger](classes/azurelogger.md)*
















## Properties




###  authenticatedUserId




• **authenticatedUserId**: *string*









The authenticated user id. A unique and persistent string that represents each authenticated user in the service.











___





###  commonProperties




• **commonProperties**: *object*









There are properties associated to all events.








#### Type declaration:




* `[ key: string]`: any

















___





###  context




• **context**: *ApplicationInsights*









Context of Application Insights.











___





###  projectName




• **projectName**: *string*









Your project name.



















## Methods




###  init




▸ **init**(`addPageTracking?`: undefined | false | true, `pageTrackingFilter?`: string[]): *void*












Download full Application Insights script from CDN and initialize it with instrumentation key.









**Parameters:**





Name | Type | Description |
------ | ------ | ------ |
`addPageTracking?` | undefined \| false \| true | Activate page tracking by calling trackPageView method. Default value is true. |
`pageTrackingFilter?` | string[] | Filter your Network by parts of url. If url has one of this filters then it will be added to Application Insights Remote Dependencies  |







**Returns:** *void*








___





###  trackEvent




▸ **trackEvent**(`eventName`: string, `properties?`: undefined | object): *void*












Add custom event (log line).
In Azure Application Insights App search this event by this template: '{projectName}.JS.{eventName}'.









**Parameters:**





Name | Type | Description |
------ | ------ | ------ |
`eventName` | string | Custom event name. It should contains only english letters without spaces. |
`properties?` | undefined \| object | There are properties associated only to this event. This properties will be added to Event Custom Properties.  |







**Returns:** *void*








___





###  trackException




▸ **trackException**(`exception`: Error, `properties?`: undefined | object): *void*












Add exception.
In Azure Application Insights App search this event by this template: '{projectName}.JS.Exception'.









**Parameters:**





Name | Type | Description |
------ | ------ | ------ |
`exception` | Error | JS/TS exception. |
`properties?` | undefined \| object | There are properties associated only to this event. This properties will be added to Event Custom Properties.  |







**Returns:** *void*








___





###  trackPageView




▸ **trackPageView**(`pageTrackingFilter?`: string[], `properties?`: undefined | object): *void*












Logs user session info about browser, network requests, etc.
In Azure Application Insights App search this event by this template: '{projectName}.JS.PageView'.









**Parameters:**





Name | Type | Description |
------ | ------ | ------ |
`pageTrackingFilter?` | string[] | Filter your Network by parts of url. If url has one of this filters then it will be added to Application Insights Remote Dependencies |
`properties?` | undefined \| object | There are properties associated only to this event. This properties will be added to Event Custom Properties.  |







**Returns:** *void*














