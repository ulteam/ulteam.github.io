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
          height={this.state.height}
          width={this.state.width}
          photoPlaceholder={placeholder}
          text={'Main text'}
          secondaryText={'Secondary text'}
        >
          My additional html
        </ImageTile>
      </div>
    );
  }

  public handleHeight = (value: number) => {
    this.setState({ height: value });
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
 | height |  |  *number \| string* |     Image height. Standard CSS height property       |  
 | photo | `Optional` |  *string* |     Image url       |  
 | photoPlaceholder |  |  *string* |     Define placeholder url, if Image is not exist       |  
 | secondaryText | `Optional` |  *string* |     Secondary text to display, usually the user first name       |  
 | style | `Optional` |  *CSSProperties* |     Add custom standard styles to component       |  
 | text | `Optional` |  *string* |     Main text to display, usually the user last name       |  
 | width |  |  *number \| string* |     Image width. Standard CSS width property       |
