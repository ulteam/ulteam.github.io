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
import { Toggle } from 'office-ui-fabric-react/lib/components/Toggle/Toggle';

interface ITestPaginationDotsState {
  arrowFontSize: number;
  dotCount: number;
  dotFontSize: number;
  isShimmer: boolean;
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
      dotFontSize: 13,
      isShimmer: false
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
        <Toggle label="Enable shimmer" onText="On" offText="Off" 
          onChange={this.handleIsShimmer}
          defaultChecked={this.state.isShimmer}
        />
        <div className="emptyHeight"></div>
        <PaginationDots
          activeDotIndex={0}
          addArrows={true}
          arrowFontSize={this.state.arrowFontSize}
          dotCount={this.state.dotCount}
          dotFontSize={this.state.dotFontSize}
          isShimmer={this.state.isShimmer}
          onClick={this.handleOnClick}
        />
      </div>
    );
  }

  private handleIsShimmer = (event: React.MouseEvent<HTMLElement, MouseEvent>, checked?: boolean | undefined) => {
    this.setState({
      isShimmer: checked ? checked : false
    });
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
 | hideArrowOnLastAndFirstPage | `Optional` |  *boolean* |     Activate this option if you want to hide left arrow on the first page and right arrow on the last page       |  
 | isShimmer | `Optional` |  *boolean* |     Enable shimmer mode       |  
 | onClick | `Optional` |  *function* |     Set custom behavior       |  
 | style | `Optional` |  *CSSProperties* |     Add custom standard styles to component       |
