---
title: ulteam-react ImageTile
permalink: /npm/ulteam-react/imagetile/
---

## ImageTile component

Tile with image and data

### Demo
Try component on the [demo](/npm/ulteam-react/demo/?r=imagetile)

### Sample

```js
import * as React from 'react';
import { ImageTile } from '../../../../common/components/ImageTile/ImageTile';
import { Slider } from 'office-ui-fabric-react/lib/components/Slider/Slider';

interface ITestImageTileState {
  height: number;
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
        <ImageTile
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
      </div>
    );
  }

  public handleHeight = (value: number) => {
    this.setState({ height: value });
  }

  public handleOnClick = (id?: number | string) => {
    console.log(`click on ${id}`);
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
 | id | `Optional` |  *number \| string* |     Tile id. Use prop for onClick callback       |  
 | maxHeight | `Optional` |  *number \| string* |     Image max height. Standard CSS height property       |  
 | maxWidth | `Optional` |  *number \| string* |     Image max width. Standard CSS width property       |  
 | minHeight |  |  *number \| string* |     Image min height. Standard CSS height property       |  
 | minWidth |  |  *number \| string* |     Image min width. Standard CSS width property       |  
 | onClick | `Optional` |  *function* |     Tile onClick event       |  
 | photo | `Optional` |  *string* |     Image url       |  
 | photoPlaceholder |  |  *string* |     Define placeholder url, if Image is not exist       |  
 | secondaryText | `Optional` |  *string* |     Secondary text to display, usually the user first name       |  
 | style | `Optional` |  *CSSProperties* |     Add custom standard styles to component       |  
 | text | `Optional` |  *string* |     Main text to display, usually the user last name       |  
 | tileTitle | `Optional` |  *string* |     Define standard title attribute for root div       |
