---
title: ulteam-react ErrorHandlerLight
permalink: /npm/ulteam-react/errorhandlerlight/
---

## ErrorHandlerLight component

Error handling component. Wrap your JSX as try catch. You can customize UI by onErrorRender callback function.

### Demo
Try component on the [demo](/npm/ulteam-react/demo/?r=errorhandlerlight)

### Sample

```tsx
import * as React from 'react';
import { ThrowErrorComponent } from '../ThrowErrorComponent/ThrowErrorComponent';
import { ErrorHandlerLight } from '../../../../common/components/ErrorHandlerLight/ErrorHandlerLight';
import { Toggle } from 'office-ui-fabric-react/lib/components/Toggle/Toggle';
import { IErrorDetails } from '../../../../common/components/ErrorHandlerLight/ErrorHandlerLight.types';

interface ITestErrorHandlerLightState {
  checkedOnErrorRender: boolean;
}

/**
 * Debug common components
 */
export class TestErrorHandlerLight extends React.Component<{}, ITestErrorHandlerLightState> {
  constructor (props: {}) {
    super(props);
    this.state = {
      checkedOnErrorRender: false
    }
  }

  public render() {
    const {checkedOnErrorRender} = this.state;
    return (
      <div>
        <Toggle label="Use onErrorRender callback function" onText="On" offText="Off" 
          onChange={this.handleOnErrorRender}
          defaultChecked={checkedOnErrorRender}
        />
        <ErrorHandlerLight onErrorRender={checkedOnErrorRender ? this.onErrorRender : undefined}>
          <ThrowErrorComponent/>
        </ErrorHandlerLight>
      </div>
    );
  }

  public handleOnErrorRender = (event: React.MouseEvent<HTMLElement, MouseEvent>, checked?: boolean | undefined) => {
    this.setState({ checkedOnErrorRender: checked === true });
  }

  public onErrorRender = (errorDetails: IErrorDetails): JSX.Element | JSX.Element[] => {
    return (
      <div className="ul-errorHandlerLight" style={{ 
        background: 'rgb(253, 200, 200)',
        padding: '8px 12px',
        fontSize: '12px',
        lineHeight: '16px',
        whiteSpace: 'pre-wrap'
       }}>
        <div>
          <span style={{ fontWeight: 600 }}>Error: </span>
          <span>
            {errorDetails.message}
          </span>
          <span style={{ opacity: 0.5 }}>
            <span style={{ fontWeight: 600 }}>. Stack: </span>
            <span>
              {errorDetails.stack}
            </span>
            <span style={{ fontWeight: 600 }}>. Info: </span>
            <span>{JSON.stringify(errorDetails.errorInfo)}</span>
          </span>
        </div>
      </div>
    );
  }
}
```


### IErrorHandlerLightProps

| Property Name | Required | Type | Comments |
|-|-|-|-|
 | onError | `Optional` |  *function* |     Handle your errors.       |  
 | onErrorRender | `Optional` |  *function* |     Render your error instead of brokened component       |
