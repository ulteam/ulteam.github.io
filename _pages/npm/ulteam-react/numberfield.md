---
title: ulteam-react NumberField
permalink: /npm/ulteam-react/numberfield/
---

## NumberField component

Component is based on TextField from [office-ui-fabric-react](https://www.npmjs.com/package/office-ui-fabric-react) package.
Properties extends TextField component props.

### Demo
Try component on the [demo](/npm/ulteam-react/demo/?r=numberfield)

### Sample

```tsx
import { Toggle } from 'office-ui-fabric-react/lib/components/Toggle/Toggle';
import * as React from 'react';
import { NumberField } from '../../../../common/components/NumberField/NumberField';

interface ITestNumberFieldState {
  useCommaDelimiter: boolean;
}

/**
 * Debug common components
 */
export class TestNumberField extends React.Component<{}, ITestNumberFieldState> {
  private fieldRef: React.RefObject<any>;

  constructor(props: {}) {
    super(props);
    this.fieldRef = React.createRef();

    this.state = {
      useCommaDelimiter: true
    }
  }
  
  public render() {
    return (
      <div style={ {maxWidth: 400} }>
        <Toggle label="Use comma delimiter" onText="On" offText="Off" 
          onChange={this.handleUseCommaDelimiter}
          defaultChecked={this.state.useCommaDelimiter}
        />
        <div className="emptyHeight"></div>
        <NumberField 
          componentRef={this.fieldRef}
          label="Number Field Label"
          autoValidation={true}
          round={3}
          onChange={this.onChangeNumberField}
          useCommaDelimiter={this.state.useCommaDelimiter}
        />
      </div>
    );
  }

  private handleUseCommaDelimiter = (event: React.MouseEvent<HTMLElement, MouseEvent>, checked?: boolean | undefined) => {
    this.setState({
      useCommaDelimiter: checked ? checked : false
    });
  }

  public onChangeNumberField = (event: React.FormEvent<HTMLInputElement | HTMLTextAreaElement>, newValue?: string | number | undefined) => {
    console.log(`Number field value = ${newValue}`);
  }
}
```


### INumberFieldProps

| Property Name | Required | Type | Comments |
|-|-|-|-|
 | autoValidation | `Optional` |  *boolean* |     Activate auto validation number value Activate number validation       |  
 | isNotValidErrorMessage | `Optional` |  *string* |     Error message if value is not valid number       |  
 | onChange |  |  *function* |  |  
 | round | `Optional` |  *number* |     Set number with round to 'x' decimal places as string value. Integer value by default Type decimal place count for number rounding       |  
 | useCommaDelimiter | `Optional` |  *boolean* |     If value is true, component will be use ',' in decimal numbers If value is true, component will be use ',' in decimal numbers       |
