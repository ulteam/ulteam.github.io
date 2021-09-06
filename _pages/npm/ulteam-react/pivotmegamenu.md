---
title: ulteam-react PivotMegaMenu
permalink: /npm/ulteam-react/pivotmegamenu/
---

## PivotMegaMenu component

Pivot with Mega Menu on each item.

### Demo
Try component on the [demo](/npm/ulteam-react/demo/?r=pivotmegamenu)

### Sample

```tsx
import { Toggle } from 'office-ui-fabric-react/lib/components/Toggle/Toggle';
import * as React from 'react';
import { PivotMegaMenu } from '../../../../common/components/PivotMegaMenu/PivotMegaMenu';
import { IPivotMegaMenuItem } from '../../../../common/components/PivotMegaMenu/PivotMegaMenu.types';

interface ITestPivotMegaMenuState {
  openOnHover: boolean;
}

/**
 * Debug common components
 */
export class TestPivotMegaMenu extends React.Component<{}, ITestPivotMegaMenuState> {
  private items: IPivotMegaMenuItem[] = [];

  constructor(props: {}) {
    super(props);
    this.state = {
      openOnHover: false
    };
    this.items = Array(5).fill(1).map((pValue, pIndex) => {
      const item: IPivotMegaMenuItem = {
        key: `pivotItem${pIndex}`,
        label: `Menu Item ${pIndex}`,
        items: Array(5).fill(1).map((value, index) => {
          return {
            key: index,
            label: `Menu Item ${pIndex}.${index}`,
            content: this.getMenuItemContent(`${pIndex}.${index}`)
          };
        })
      };

      return item;
    });
  }
  
  public render() {
    return (
      <div>
        <Toggle label="Open on hover" onText="On" offText="Off" 
          onChange={this.handleOpenOnHover}
          defaultChecked={this.state.openOnHover}
        />
        <PivotMegaMenu
          items={this.items}
          openOnHover={this.state.openOnHover}
          uniqueKey="testPivotMegaMenu"
        />
      </div>
    );
  }

  private getMenuItemContent(key: string): JSX.Element {
    return (
      <ul className="ul-megaMenu-itemList">
        {new Array(5).fill(1).map((value, index) => {
          return <li className="ul-megaMenu-item" key={`${key}.${index}`}>{`Sub menu item ${key}.${index}`}</li>
        })}
      </ul>
    ) 
  }

  private handleOpenOnHover = (event: React.MouseEvent<HTMLElement, MouseEvent>, checked?: boolean | undefined) => {
    this.setState({
      openOnHover: checked === true
    });
  }
}
```


### IPivotMegaMenuProps

| Property Name | Required | Type | Comments |
|-|-|-|-|
 | className | `Optional` |  *string* |     Add custom class to component       |  
 | items |  |  *IPivotMegaMenuItem[]* |     Pivot items with children items for Mega Menu component       |  
 | openOnHover | `Optional` |  *boolean* |     Whether open Mega Menu on hover or on click       |  
 | style | `Optional` |  *CSSProperties* |     Add custom standard styles to component       |  
 | uniqueKey |  |  *string* |     Unique for DOM identificator       |
