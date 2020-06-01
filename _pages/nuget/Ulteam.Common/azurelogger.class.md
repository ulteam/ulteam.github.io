---
title: Ulteam.Common 
permalink: /nuget/Ulteam.Common/azurelogger/
sidebar:
  nav: "nuget"
---

### AzureLogger Class
Namespace: Ulteam.Common.Logger

#### Description
Work with Azure Application Insights.

#### Constructors

| Name | Description |
|-|-|
| AzureLogger(String instrumentationKey, String projectName, String serviceName, String authenticatedUserId, String commonProperties, String} initContext, Boolean ) | Set configuration.  <br> **instrumentationKey**: *Azure Application Insight App instrumentation key.*  <br> **projectName**: *Your project name. Name should be contain only english letters and 'dot' char. For example: 'SampleProject'.*  <br> **serviceName**: *Your service name or type. For example: WebJob, HttpService, etc.*  <br> **authenticatedUserId**: *The authenticated user id. A unique and persistent string that represents each authenticated user in the service.              It should not contain commas, semi-colons, equal signs, spaces, or vertical-bars.*  <br> **commonProperties**: *There are properties associated to all events, like ListItem.Id. This properties will be added to Event Custom Properties.*  <br> **initContext**: *Run Init() method authomatically.*  |

#### Methods

| Name | Description |
|-|-|
| Dispose() | Dispose object.  |
| Init() | Initialize operation telemetry and create Operation with Id and Name.              All events on this session will be searched in App Insights by one Operation Id.  |
| TrackEvent(String eventName, String properties, String} metrics, String , Double} ) | Add custom event (log line).             In Azure Application Insights App search this event by this template: '{projectName}.{serviceName}.{eventName}'.  <br> **eventName**: *Custom event name.              It should contains only english letters without spaces.*  <br> **properties**: *There are properties associated only to this event. This properties will be added to Event Custom Properties.*  <br> **metrics**: *Measurements associated with this event.*  |
| TrackException(Exception exception, String properties, String} metrics, String , Double} ) | Send custom event with name like {projectName}.{serviceName}.Exception and             send an Microsoft.ApplicationInsights.DataContracts.ExceptionTelemetry for display             in Diagnostic Search.  <br> **exception**: *The exception to log.*  <br> **properties**: *There are properties associated only to this event. This properties will be added to Event Custom Properties.*  <br> **metrics**: *Measurements associated with this event.*  |
| ConcatProperties(String properties, String} ) | Concatenate properties with AzureLogger.CommonProperties.  <br> **properties**: *Properties for concatenation.*  |

#### Samples
```csharp

public void SampleTestWithUsing()
{
    // you can add your custom properties which are showing in App Insights Event Custom Properties
    Dictionary<string, string> customProperties = new Dictionary<string, string>
    {
        { "itemId", "123" }
    };

    using (AzureLogger azureLogger = new AzureLogger(instrumentationKey: "your_key_value",
                                                     projectName: "Ulteam.Common",
                                                     serviceName: "SampleService",
                                                     authenticatedUserId: "user@sample.com",
                                                     commonProperties: customProperties))
    {
        try
        {
            azureLogger.TrackEvent("Start");

            // you can add custom metrics such as job working time
            Stopwatch watch = Stopwatch.StartNew();

            // --------------------------
            // write your awesome code!!!
            // --------------------------

            watch.Stop();

            Dictionary<string, double> metrics = new Dictionary<string, double>
            {
                { "serviceWorkDuration", watch.ElapsedMilliseconds }
            };
            azureLogger.TrackEvent(eventName: "Finish", metrics: metrics);
        }
        catch (Exception ex)
        {
            azureLogger.TrackException(ex);
        }
    }
}
```
