---
title: ulteam-react Slider
permalink: /npm/ulteam-react/slider/
---

## Slider component

Horizontal slider with animation.

### Demo
Try component on the [demo](/npm/ulteam-react/demo/?r=slider)

### Sample

```tsx
import * as React from 'react';
import { ImageTile } from '../../../../common/components/ImageTile/ImageTile';
import { Slider } from '../../../../common/components/Slider/Slider';
import { SliderPaginationType } from '../../../../common/components/Slider/Slider.types';
import { Slider as OfficeUiSlider} from 'office-ui-fabric-react/lib/components/Slider/Slider';
import { Dropdown } from 'office-ui-fabric-react/lib/components/Dropdown/Dropdown';
import { IDropdownOption } from 'office-ui-fabric-react/lib/components/Dropdown/Dropdown.types';

interface ITestSliderState {
  arrowFontSize: number;
  dotFontSize: number;
  itemCount: number;
  paginationType: SliderPaginationType;
  scrollBy: number;
  showCount: number;
  transitionDuration: number;
}

/**
 * Test Slider component
 */
export class TestSlider extends React.Component<{}, ITestSliderState> {
  private itemWidth = 150;
  private itemPadding = 4;
  private placeholder = `https://via.placeholder.com/${this.itemWidth}x${this.itemWidth}`;

  constructor(props: {}) {
    super(props);

    this.state = {
      arrowFontSize: 20,
      dotFontSize: 13,
      itemCount: 25,
      paginationType: SliderPaginationType.ArrowsAndDots,
      scrollBy: 3,
      showCount: 5,
      transitionDuration: 0.5
    };
  }
  
  public render() {
    return (
      <div>
        <h3>Slider component</h3>
        <OfficeUiSlider
          label="Arrow font size"
          min={5}
          max={40}
          step={1}
          defaultValue={this.state.arrowFontSize}
          showValue={true}
          onChange={(value: number) => {this.setState({arrowFontSize: value})} }
        />
        <OfficeUiSlider
          label="Dot font size"
          min={5}
          max={30}
          step={1}
          defaultValue={this.state.dotFontSize}
          showValue={true}
          onChange={(value: number) => {this.setState({dotFontSize: value})} }
        />
        <OfficeUiSlider
          label="Number of items for scrolling"
          min={1}
          max={5}
          step={1}
          defaultValue={this.state.scrollBy}
          showValue={true}
          onChange={(value: number) => {this.setState({scrollBy: value})} }
        />
        <OfficeUiSlider
          label="Number of items"
          min={1}
          max={50}
          step={1}
          defaultValue={this.state.itemCount}
          showValue={true}
          onChange={(value: number) => {this.setState({itemCount: value})} }
        />
        <OfficeUiSlider
          label="Number of items to display"
          min={5}
          max={8}
          step={1}
          defaultValue={this.state.showCount}
          showValue={true}
          onChange={(value: number) => {this.setState({showCount: value})} }
        />
        <OfficeUiSlider
          label="Animation transition duration in seconds"
          min={0.1}
          max={2}
          step={0.1}
          defaultValue={this.state.transitionDuration}
          showValue={true}
          onChange={(value: number) => {this.setState({transitionDuration: value})} }
        />
        <Dropdown
          label="Pagination type"
          placeholder="ArrowsAndDots"
          options={[
            {
              key: 'ArrowsAndDots',
              text: 'ArrowsAndDots'
            },
            {
              key: 'Arrows',
              text: 'Arrows'
            },
            {
              key: 'Dots',
              text: 'Dots'
            }
          ]}
          onChange={this.handleOnChangeType}
          style={ {width: 180} }
        />
        <div className="emptyHeight"></div>
        
        <Slider
          itemWidth={this.itemWidth + this.itemPadding * 2}
          items={this.getItems()}
          arrowFontSize={this.state.arrowFontSize}
          dotFontSize={this.state.dotFontSize}
          paginationType={this.state.paginationType}
          scrollBy={this.state.scrollBy}
          showCount={this.state.showCount}
          transitionDuration={this.state.transitionDuration}
        />
      </div>
    );
  }

  public getItems(): JSX.Element[] {
    const result: JSX.Element[] = [];

    const style = { padding: this.itemPadding }
    
    for (let i = 0; i < this.state.itemCount; i++) {
      result.push((
        <ImageTile
          key={i}
          maxHeight={this.itemWidth}
          maxWidth={this.itemWidth}
          minHeight={this.itemWidth}
          minWidth={this.itemWidth}
          id={i}
          photoPlaceholder={this.placeholder}
          onClick={this.handleOnClick}
          text={`Main text ${i}`}
          secondaryText={`Secondary text ${i}`}
          style={style}
        />
      ));
    }

    return result;
  }

  public handleOnChangeType = (event: any, option?: IDropdownOption | undefined) => {
    if (option && option.key) {
      const paginationType = option.key.toString() as SliderPaginationType;
      this.setState({ paginationType });
    }
  }

  public handleOnClick = (id?: number | string) => {
    console.log(`click on ${id}`);
  }
}
```


### ISliderProps

| Property Name | Required | Type | Comments |
|-|-|-|-|
 | arrowFontSize | `Optional` |  *number* |     Pagination arrow font size in pixels       |  
 | className | `Optional` |  *string* |     Add custom class to component       |  
 | defaultPageIndex | `Optional` |  *number* |     Set default page integer index       |  
 | dotFontSize | `Optional` |  *number* |     Pagination dot font size in pixels if paginationType is SliderPaginationType.ArrowsAndDots       |  
 | itemWidth |  |  *number* |     An item width including paddings and margins       |  
 | items |  |  *Element[]* |     All slider's elements       |  
 | paginationClassName | `Optional` |  *string* |     Add your own class to pagination controls       |  
 | paginationStyle | `Optional` |  *CSSProperties* |     Add your own style to pagination controls       |  
 | paginationType | `Optional` |  *SliderPaginationType* |     Select pagination type.      **`default`** SliderPaginationType.Dots      |  
 | scrollBy |  |  *number* |     Integer number of items for scrolling       |  
 | showCount |  |  *number* |     Integer number of items to display       |  
 | style | `Optional` |  *CSSProperties* |     Add custom standard styles to component       |  
 | transitionDuration | `Optional` |  *number* |     Animation transition duration in seconds       |
