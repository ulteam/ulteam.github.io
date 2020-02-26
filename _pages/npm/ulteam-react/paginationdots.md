---
title: ulteam-react PaginationDots
permalink: /npm/ulteam-react/paginationdots/
---

## PaginationDots component

Pagination dots with or not arrows.

### Demo
Try component on the [demo](/npm/ulteam-react/demo/?r=paginationdots)

### Sample

```tsx
import * as React from 'react';
import { PaginationDots } from '../../../../common/components/PaginationDots/PaginationDots';
import { Slider } from 'office-ui-fabric-react/lib/components/Slider/Slider';

interface ITestPaginationDotsState {
  arrowFontSize: number;
  dotCount: number;
  dotFontSize: number;
}

/**
 * Test PaginationDots component
 */
export class TestPaginationDots extends React.Component<{}, ITestPaginationDotsState> {
  constructor(props: {}) {
    super(props);

    this.state = {
      arrowFontSize: 16,
      dotCount: 10,
      dotFontSize: 13
    };
  }
  
  public render() {
    return (
      <div>
        <h3>PaginationDots component</h3>
          <Slider
            label="Dot count"
            min={3}
            max={20}
            step={1}
            defaultValue={this.state.dotCount}
            showValue={true}
            onChange={(value: number) => {this.setState({dotCount: value})}}
          />
          <Slider
            label="Arrow font size"
            min={5}
            max={40}
            step={1}
            defaultValue={this.state.arrowFontSize}
            showValue={true}
            onChange={(value: number) => {this.setState({arrowFontSize: value})}}
          />
          <Slider
            label="Dot font size"
            min={5}
            max={30}
            step={1}
            defaultValue={this.state.dotFontSize}
            showValue={true}
            onChange={(value: number) => {this.setState({dotFontSize: value})}}
          />
        <div className="emptyHeight"></div>
        <PaginationDots
          activeDotIndex={0}
          addArrows={true}
          arrowFontSize={this.state.arrowFontSize}
          dotCount={this.state.dotCount}
          dotFontSize={this.state.dotFontSize}
          onClick={this.handleOnClick}
        />
      </div>
    );
  }

  public handleOnClick = (dotIndex: number) => {
    console.log(`click on ${dotIndex} dot`);
  }
}
```


### IPaginationDotsProps

| Property Name | Required | Type | Comments |
|-|-|-|-|
 | activeDotIndex | `Optional` |  *number* |     Set active dot index       |  
 | addArrows | `Optional` |  *boolean* |     Add left and right arrows       |  
 | arrowFontSize | `Optional` |  *number* |     Arrow font size in pixels       |  
 | className | `Optional` |  *string* |     Add custom class to component       |  
 | dotCount |  |  *number* |     Number of dots or pages       |  
 | dotFontSize | `Optional` |  *number* |     Dot font size in pixels       |  
 | onClick | `Optional` |  *function* |     Set custom behavior       |  
 | style | `Optional` |  *CSSProperties* |     Add custom standard styles to component       |
