---
title: ulteam-react ErrorHandler
permalink: /npm/ulteam-react/errorhandler/
---

## ErrorHandler component

Error handling component. Wrap your JSX as try catch. Exception view based on MessageBar from [office-ui-fabric-react](https://www.npmjs.com/package/office-ui-fabric-react) package.

### Demo
Try component on the [demo](/npm/ulteam-react/demo/?r=errorhandler)

### Sample

```js
import * as React from 'react';
import { AzureLogger } from 'ulteam-scripts/lib';
import { ErrorHandler } from '../../../..';
import { ThrowErrorComponent } from '../ThrowErrorComponent/ThrowErrorComponent';

/**
 * Debug common components
 */
export class TestErrorHandler extends React.Component<{}, {}> {
  private azureLogger: AzureLogger;
  constructor(props: {}) {
    super(props);

    this.azureLogger = new AzureLogger(
      'c7310ee5-8c8f-4c26-87b5-f166c9c4e8a8',
      'user@sample.com',
      'ulteam.react'
    );
    this.azureLogger.init();
  }
  
  public render() {
    return (
      <div>
        <div>
          <ErrorHandler azureLogger={this.azureLogger} messageBarProps={{ isMultiline: true }}>
            <ThrowErrorComponent />
          </ErrorHandler>
        </div>
      </div>
    );
  }
}
```


### IErrorHandlerProps

| Property Name | Required | Type | Comments |
|-|-|-|-|
 | azureLogger | `Optional` |  *AzureLogger* |     It's used for adding exception to Azure Application Insights.       |  
 | messageBarProps | `Optional` |  *IMessageBarProps* |     Define your own props for Office UI MessageBar component       |  
 | onError | `Optional` |  *function* |     Handle your errors.       |
