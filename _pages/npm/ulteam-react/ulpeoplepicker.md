---
title: ulteam-react UlPeoplePicker
permalink: /npm/ulteam-react/ulpeoplepicker/
---

## UlPeoplePicker component

People picker based on NormalPeoplePicker component from [office-ui-fabric-react](https://www.npmjs.com/package/office-ui-fabric-react) package.
It's just more convenient NormalPeoplePicker component.


### Sample

```tsx
import * as React from 'react';
import { UlPeoplePicker } from '../../../../controls/components/UlPeoplePicker/UlPeoplePicker';
import { IUPersonaProps } from '../../../../controls/components/UlPeoplePicker/UlPeoplePicker.types';

export class TestUlPeoplePicker extends React.Component<{}, {}> {
  private users: IUPersonaProps[] = [];
  constructor(props: {}) {
    super(props);

    this.users = this.getUsers();
  }

  public render() {
    return (
      <div style={{ maxWidth: 400 }}>
        <UlPeoplePicker
          fieldName="customFieldName"
          itemLimit={3}
          label="People picker label"
          noResultsFoundText="No results. Start type with 'User'"
          resolveDelay={300}
          onResolveSuggestions={this.onResolveSuggestions}
        />
      </div>
    );
  }

  /** Mock users */
  private getUsers(): IUPersonaProps[] {
    const result: IUPersonaProps[] = [];
    for(let i = 0; i < 30; i++) {
      result.push({
        id: `key${i}`,
        text: `User Name ${i}`
      });
    }
    return result;
  }

  private onResolveSuggestions = async (filterText: string, currentPersonas: IUPersonaProps[], limitResults?: number | undefined): Promise<IUPersonaProps[]> => {
    // your async API request
    await this.delay(300);

    const result: IUPersonaProps[] = filterText.length > 0 ?
      this.users.filter(x => x.text && x.text.toLowerCase().indexOf(filterText.toLowerCase()) > -1) :
      [];

    return result;
  }

  private async delay(ms: number): Promise<void> {
    return new Promise( resolve => setTimeout(resolve, ms) );
  }
}
```


### IUlPeoplePickerProps

| Property Name | Required | Type | Comments |
|-|-|-|-|
 | customClassName | `Optional` |  *string* |     Class name which added to Office Ui Picker control       |  
 | defaultSelectedItems | `Optional` |  *IUPersonaProps[]* |     Default values       |  
 | disabled | `Optional` |  *boolean* |     Flag for disabling the picker       |  
 | errorMessage | `Optional` |  *string* |     Text displayed below the control       |  
 | fieldName |  |  *string* |     Field name. It returns in handleChangeValues callback function       |  
 | handleChangeValues | `Optional` |  *function* |  |  
 | itemLimit |  |  *number* |     Restrict the amount of selectable items       |  
 | label | `Optional` |  *string* |     Field label       |  
 | noResultsFoundText | `Optional` |  *string* |     The text that should appear if no results are found when searching       |  
 | onResolveSuggestions |  |  *function* |     A callback for what should happen when a person types text into the input. Returns the already selected items so the resolver can filter them out. If used in conjunction with resolveDelay this will ony kick off after the delay throttle.       |  
 | required | `Optional` |  *boolean* |     If field is required       |  
 | resolveDelay | `Optional` |  *number* |     The delay time in ms before resolving suggestions, which is kicked off when input has been changed. e.g. If a second input change happens within the resolveDelay time, the timer will start over. Only until after the timer completes will onResolveSuggestions be called.       |  
 | suggestionProps | `Optional` |  *IUBasePickerSuggestionsProps* |     Consts for suggestion list       |
