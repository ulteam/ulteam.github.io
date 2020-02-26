---
title: ulteam-react UlEvent
permalink: /npm/ulteam-react/ulevent/
---

## UlEvent component

Event with calendar tile.

### Demo
Try component on the [demo](/npm/ulteam-react/demo/?r=ulevent)

### Sample

```tsx
import * as React from 'react';
import { UlEvent } from '../../../../common/components/UlEvent/UlEvent';
import { Toggle } from 'office-ui-fabric-react/lib/components/Toggle/Toggle';
import { UlEventMonthLocale } from '../../../../common/components/UlEvent/UlEvent.types';

interface ITestImageTileState {
  useLongMonth: boolean;
  useRuLocale: boolean;
}

/**
 * Test Event component
 */
export class TestUlEvent extends React.Component<{}, ITestImageTileState> {
  constructor(props: {}) {
    super(props);

    this.state = {
      useLongMonth: false,
      useRuLocale: false
    }
  }
  
  public render() {
    return (
      <div>
      <h3>UlEvent component</h3>
        <Toggle label="Use long month" onText="On" offText="Off" 
          onChange={this.handleUseLongMonth}
          defaultChecked={this.state.useLongMonth}
        />
        <Toggle label="Use RU locale" onText="On" offText="Off" 
          onChange={this.handleUseRuLocale}
          defaultChecked={this.state.useRuLocale}
        />
        <div className="emptyHeight"></div>

        <UlEvent 
          date={new Date()} 
          monthLocale={this.state.useRuLocale === true ? UlEventMonthLocale.Ru : undefined}
          title="Today event title"
          useLongMonth={this.state.useLongMonth}
        >
          <div>Additional info...</div>
        </UlEvent>
      </div>
    );
  }

  private handleUseLongMonth = (event: React.MouseEvent<HTMLElement, MouseEvent>, checked?: boolean | undefined) => {
    if (checked !== undefined) {
      this.setState({ useLongMonth: checked })
    }
  }

  private handleUseRuLocale = (event: React.MouseEvent<HTMLElement, MouseEvent>, checked?: boolean | undefined) => {
    if (checked !== undefined) {
      this.setState({ useRuLocale: checked })
    }
  }
}
```


### IUlEventProps

| Property Name | Required | Type | Comments |
|-|-|-|-|
 | className | `Optional` |  *string* |     Add custom class to component       |  
 | customLocale | `Optional` |  *string[]* |     You might use your own month names. Just set string array.       |  
 | date |  |  *Date* |     Event date       |  
 | monthLocale | `Optional` |  *UlEventMonthLocale* |     Choose predefined locale for month names       |  
 | style | `Optional` |  *CSSProperties* |     Add custom standard styles to component       |  
 | title | `Optional` |  *string* |     Event title text       |  
 | useLongMonth | `Optional` |  *boolean* |     Whether using long month names or not       |
