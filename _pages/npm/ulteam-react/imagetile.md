---
title: ulteam-react ImageTile
permalink: /npm/ulteam-react/imagetile/
---

## ImageTile component

Tile with image and data.

### Demo
Try component on the [demo](/npm/ulteam-react/demo/?r=imagetile)

### Sample

```tsx
import * as React from 'react';
import { ImageTile } from '../../../../common/components/ImageTile/ImageTile';
import { Slider } from 'office-ui-fabric-react/lib/components/Slider/Slider';
import { Toggle } from 'office-ui-fabric-react/lib/components/Toggle/Toggle';

interface ITestImageTileState {
  height: number;
  isShimmer: boolean;

  openLinkInNewTab?: boolean;

  width: number;
}

/**
 * Test ImageTile component
 */
export class TestImageTile extends React.Component<{}, ITestImageTileState> {
  constructor(props: {}) {
    super(props);

    this.state = {
      height: 150,
      isShimmer: false,
      width: 150
    }
  }
  
  public render() {
    const placeholder = `https://via.placeholder.com/${this.state.width}x${this.state.height}`;

    return (
      <div>
        <Slider
          label="Image width"
          min={100}
          max={300}
          step={10}
          defaultValue={150}
          showValue={true}
          onChange={this.handleWidth}
        />
        <Slider
          label="Image height"
          min={100}
          max={300}
          step={10}
          defaultValue={150}
          showValue={true}
          onChange={this.handleHeight}
        />
        <Toggle label="Enable shimmer" onText="On" offText="Off" 
          onChange={this.handleIsShimmer}
          defaultChecked={this.state.isShimmer}
        />
        <Toggle label="Open link in new tab" onText="On" offText="Off" 
          onChange={this.handleOpenLinkInNewTag}
          defaultChecked={this.state.openLinkInNewTab}
        />
        <div className="emptyHeight"></div>
        <ImageTile
          key={1}
          href={this.state.openLinkInNewTab === true ? 'https://google.com' : undefined}
          target={this.state.openLinkInNewTab === true ? '_blank' : undefined}
          isShimmer={this.state.isShimmer}
          maxHeight={this.state.height}
          maxWidth={this.state.width}
          minHeight={this.state.height}
          minWidth={this.state.width}
          id="my image tile"
          onClick={this.handleOnClick}
          photoPlaceholder={placeholder}
          tileTitle="My title"
          text="Main text"
          secondaryText="Secondary text"
        >
          My additional html
        </ImageTile>
        <h3>ImageTile without image</h3>
        <ImageTile
          key={2}
          href={this.state.openLinkInNewTab === true ? 'https://google.com' : undefined}
          target={this.state.openLinkInNewTab === true ? '_blank' : undefined}
          isShimmer={this.state.isShimmer}
          maxHeight={this.state.height}
          maxWidth={this.state.width}
          minHeight={this.state.height}
          minWidth={this.state.width}
          id="my image tile"
          onClick={this.handleOnClick}
          photo="/wrong/url"
          tileTitle="My title"
          text="Main text"
          secondaryText="Secondary text"
        ></ImageTile>
      </div>
    );
  }

  public handleHeight = (value: number) => {
    this.setState({ height: value });
  }

  private handleIsShimmer = (event: React.MouseEvent<HTMLElement, MouseEvent>, checked?: boolean | undefined) => {
    this.setState({
      isShimmer: checked ? checked : false
    });
  }

  public handleOnClick = (id?: number | string) => {
    console.log(`click on ${id}`);
  }

  private handleOpenLinkInNewTag = (event: React.MouseEvent<HTMLElement, MouseEvent>, checked?: boolean | undefined) => {
    this.setState({ openLinkInNewTab: checked });
  }

  public handleWidth = (value: number) => {
    this.setState({ width: value });
  }
}
```


### IImageTileProps

| Property Name | Required | Type | Comments |
|-|-|-|-|
 | className | `Optional` |  *string* |     Add custom class to component       |  
 | href | `Optional` |  *string* |     Standard 'a' tag href attribute for title and description       |  
 | id | `Optional` |  *number \| string* |     Tile id. Use prop for onClick callback       |  
 | isShimmer | `Optional` |  *boolean* |     Enable shimmer mode       |  
 | maxHeight | `Optional` |  *number \| string* |     Image max height. Standard CSS height property       |  
 | maxWidth | `Optional` |  *number \| string* |     Image max width. Standard CSS width property       |  
 | minHeight |  |  *number \| string* |     Image min height. Standard CSS height property       |  
 | minWidth |  |  *number \| string* |     Image min width. Standard CSS width property       |  
 | onClick | `Optional` |  *function* |     Tile onClick event       |  
 | photo | `Optional` |  *string* |     Image url       |  
 | photoPlaceholder | `Optional` |  *string* |     Define placeholder url, if Image is not exist       |  
 | secondaryText | `Optional` |  *string* |     Secondary text to display, usually the user first name       |  
 | style | `Optional` |  *CSSProperties* |     Add custom standard styles to component       |  
 | target | `Optional` |  *string* |     Standard 'a' tag target attribute for title and description       |  
 | text | `Optional` |  *string* |     Main text to display, usually the user last name       |  
 | tileTitle | `Optional` |  *string* |     Define standard title attribute for root div       |
