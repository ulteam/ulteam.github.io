---
title: ulteam-react BurgerMenu
permalink: /npm/ulteam-react/burgermenu/
---

## BurgerMenu component

The Burger Menu component.

### Demo
Try component on the [demo](/npm/ulteam-react/demo/?r=burgermenu)

### Sample

```tsx
import { PanelType } from 'office-ui-fabric-react/lib/components/Panel/Panel.types';
import { IconButton } from 'office-ui-fabric-react/lib/components/Button/IconButton/IconButton';
import * as React from 'react';
import { BurgerMenu } from '../../../../common/components/BurgerMenu/BurgerMenu';
import { IBurgerMenuItem } from '../../../../common/components/BurgerMenu/BurgerMenu.types';

interface ITestBurgerMenuState {
  showPanel: boolean;
}

/**
 * Test Burger Menu
 */
export class TestBurgerMenu extends React.Component<{}, ITestBurgerMenuState> {
  private items: IBurgerMenuItem[] = [];

  constructor(props: {}) {
    super(props);
    this.state = {
      showPanel: false
    };
    this.items = Array(5).fill(1).map((pValue, pIndex) => {
      const item: IBurgerMenuItem = {
        key: `pivotItem${pIndex}`,
        label: `Menu Item ${pIndex}`,
        childrens: Array(5).fill(1).map((value, index) => {
          return {
            key: index,
            label: `Sub Menu Item ${pIndex}.${index}`,
            target: '_blank',
            url: 'https://google.com'
          };
        })
      };

      return item;
    });
  }
  
  public render() {
    const {showPanel} = this.state;
    return (
      <div>
        <h3>Click on me!</h3>
        <BurgerMenu
          content={this.renderContentBelow()}
          isLightDismiss
          items={this.items}
          onDismiss={() => this.setState({showPanel: false})}
          type={PanelType.smallFixedNear}
        >
          <IconButton
            iconProps={ {iconName: 'GlobalNavButton'} }
            onClick={ () => this.setState({showPanel: !showPanel}) }
          />
        </BurgerMenu>
      </div>
    );
  }

  private renderContentBelow(): JSX.Element {
    return (
      <div style={ {margin: '1rem'} }>
        <img src="https://via.placeholder.com/240x240"></img>
      </div>
    )
  }
}
```


### IBurgerMenuProps

| Property Name | Required | Type | Comments |
|-|-|-|-|
 | className | `Optional` |  *string* |     Add custom class to component       |  
 | content | `Optional` |  *React.ReactNode* |     Show this React Node below Menu on the Panel       |  
 | isLightDismiss | `Optional` |  *boolean* |     Whether the panel can be light dismissed.      **`defaultvalue`** false      |  
 | isOpenByDefault | `Optional` |  *boolean* |     Whether the panel is displayed by default.      **`defaultvalue`** false      |  
 | items |  |  *IBurgerMenuItem[]* |     Menu Items       |  
 | onBackClick | `Optional` |  *function* |     A callback function for when the back button on the panel is clicked.       |  
 | onDismiss | `Optional` |  *function* |     A callback function for when the panel is closed, before the animation completes. If the panel should NOT be dismissed based on some keyboard event, then simply call ev.preventDefault() on it       |  
 | style | `Optional` |  *CSSProperties* |     Add custom standard styles to component       |  
 | type | `Optional` |  *PanelType* |     Type of the panel.      **`defaultvalue`** PanelType.smallFixedFar      |
