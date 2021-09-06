---
title: ulteam-react MegaMenu
permalink: /npm/ulteam-react/megamenu/
---

## MegaMenu component

Mega Menu component.

### Demo
Try component on the [demo](/npm/ulteam-react/demo/?r=megamenu)

### Sample

```tsx
import { IconButton } from 'office-ui-fabric-react/lib/Button';
import * as React from 'react';
import { MegaMenu } from '../../../../common/components/MegaMenu/MegaMenu';
import { IMegaMenuItem } from '../../../../common/components/MegaMenu/MegaMenu.types';

interface ITestMegaMenuState {
  show: boolean;
}

/**
 * Debug common components
 */
export class TestMegaMenu extends React.Component<{}, ITestMegaMenuState> {
  private items: IMegaMenuItem[] = [];

  constructor(props: {}) {
    super(props);
    this.state = {
      show: true
    };
    this.items = Array(5).fill(1).map((value, index) => {
      return {
        key: index,
        label: `Menu Item ${index}`,
        content: this.getMenuItemContent(index)
      };
    });
  }
  
  public render() {
    return (
      <div>
        <MegaMenu 
          data={this.items}
          onDismiss={this.handleDismiss}
          show={this.state.show}
          uniqueKey="unique-mega-menu-id"
        >
          <div style={ {marginLeft: 10} }>
            <IconButton iconProps={ {iconName: 'GlobalNavButton'} } onClick={this.handleButtonClick}/>
          </div>
        </MegaMenu>
      </div>
    );
  }

  private getMenuItemContent(key: number): JSX.Element {
    return (
      <ul>
        {new Array(5).fill(1).map((value, index) => {
          return <li key={index}>{`Sub menu item ${key + index}`}</li>
        })}
      </ul>
    ) 
  }

  private handleButtonClick = () => {
    this.setState({ show: !this.state.show });
  }
  
  private handleDismiss = () => {
    this.setState({ show: false });
  }
}
```


### IMegaMenuProps

| Property Name | Required | Type | Comments |
|-|-|-|-|
 | className | `Optional` |  *string* |     Add custom class to component       |  
 | data |  |  *IMegaMenuItem[]* |     Menu items       |  
 | fullWidth | `Optional` |  *boolean* |     Whether open mega menu on full width       |  
 | onDismiss |  |  *function* |     Set behavior when a mouse leaves a MegaMenu       |  
 | show |  |  *boolean* |     Whether show Mega Menu or not       |  
 | style | `Optional` |  *CSSProperties* |     Add custom standard styles to component       |  
 | uniqueKey |  |  *string* |     Unique for DOM identificator       |
