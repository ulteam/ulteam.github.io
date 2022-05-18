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
import { Toggle } from 'office-ui-fabric-react/lib/components/Toggle/Toggle';

interface ITestMegaMenuState {
  fullWidth: boolean;
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
      fullWidth: false,
      show: true
    };
    this.items = Array(5).fill(1).map((value, index) => {
      return {
        key: index,
        label: `Menu Item ${index}`,
        linkUrl:`Menu Href ${index}`,
        content: this.getMenuItemContent(index)
      };
    });
  }
  
  public render() {
    return (
      <div>
        <Toggle label="Full Width" onText="On" offText="Off" 
          onChange={this.handleFullWidth}
          defaultChecked={this.state.fullWidth}
        />
        <div style={ { height: 20 } }/>
        <MegaMenu 
          data={this.items}
          fullWidth={this.state.fullWidth}
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

  private handleFullWidth = (event: React.MouseEvent<HTMLElement, MouseEvent>, checked?: boolean | undefined) => {
    this.setState({
      fullWidth: checked === true
    });
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
 | onRenderStyle | `Optional` |  *function* |     Set custom style for the Mega Menu container on the component render       |  
 | show |  |  *boolean* |     Whether show Mega Menu or not       |  
 | style | `Optional` |  *CSSProperties* |     Add custom standard styles to component       |  
 | uniqueKey |  |  *string* |     Unique for DOM identificator       |
