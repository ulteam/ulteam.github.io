---
title: ulteam-react BlogTileBoard
permalink: /npm/ulteam-react/blogtileboard/
---

## BlogTileBoard component

Blogs board based on BlogTile component.

### Sample

```js
import * as React from 'react';
import { IBlogTileData, IBlogTileBaseProps } from '../../../../common/components/BlogTile/BlogTile.types';
import { Toggle } from 'office-ui-fabric-react/lib/components/Toggle/Toggle';
import { BlogTileBoard } from '../../../../common/components/BlogTileBoard/BlogTileBoard';
import { Slider } from 'office-ui-fabric-react/lib/components/Slider/Slider';

interface ITestState {
  boardHeight: number;

  hideFooter?: boolean;

  isShimmer?: boolean;

  noFixedHeight?: boolean;

  noImage?: boolean;

  numberOfItems: number;

  scaleImageOnHover?: boolean;

  slideInBottom?: boolean;

  slideInBottomNoTitle?: boolean;
}

/**
 * Debug common components
 */
export class TestBlogTileBoard extends React.Component<{}, ITestState> {
  constructor(props: {}) {
    super(props);

    this.state = {
      boardHeight: 250,
      hideFooter: false,
      numberOfItems: 3,
      scaleImageOnHover: undefined
    };
  }

  public render() {
    const blogTileData: IBlogTileData = {
      title: 'Awesome blog tile title',
      date: '14:57 | 20.06.2020',
      description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi faucibus enim a consectetur mollis. In imperdiet venenatis urna, ut tempor augue sagittis quis. Nullam faucibus, sapien eget rutrum vehicula, ligula ex malesuada massa, eu congue turpis magna scelerisque metus. Sed gravida bibendum varius. Vivamus sed lorem dictum dolor volutpat maximus lacinia et enim. Praesent finibus, felis in consectetur sagittis, est est auctor ipsum, eu mollis orci dolor sit amet ligula. Pellentesque aliquet massa nulla, et pulvinar massa cursus ac. Nulla in mollis libero. Etiam at libero eu leo suscipit lacinia a at ligula. Quisque vel urna vehicula, efficitur sem non, convallis diam. Donec dictum vitae tortor non ullamcorper.',
      imageUrl: this.state.noImage !== true ? '/debug/mockData/photo-fullHD.jpg' : undefined,
      numberOfComments: 5,
      numberOfLikes: 6
    }

    const items: IBlogTileData[] = [];
    for (let i = 0; i < this.state.numberOfItems; i++) {
      items.push({...blogTileData});
    }

    const mainTileProps: IBlogTileBaseProps = {
      descriptionMaxSize: 200,
      hideFooter: this.state.hideFooter,
      maxWidth: 500,
      noFixedDataHeight: this.state.noFixedHeight,
      scaleImageOnHover: this.state.scaleImageOnHover,
      slideInBottom: this.state.slideInBottom,
      slideInBottomNoTitle: this.state.slideInBottomNoTitle,
      titleMaxSize: 200
    };

    return (
      <div>
          <h3>BlogTile component</h3>
          <Toggle label="Add scale animation to tile image" onText="On" offText="Off" 
            onChange={this.handleScaleImage}
            defaultChecked={this.state.scaleImageOnHover}
          />
          <Toggle label="Add slide-in-bottom animation" onText="On" offText="Off" 
            onChange={this.handleSlideInBottom}
            defaultChecked={this.state.slideInBottom}
          />
          <Toggle label="No tile image" onText="On" offText="Off" 
            onChange={this.handleNoImage}
            defaultChecked={this.state.noImage}
          />
          <Toggle label="Hide blog footer" onText="On" offText="Off" 
            onChange={this.handleHideFooter}
            defaultChecked={this.state.hideFooter}
          />
          <Toggle label="No fixed height (enable only if blog footer is hide)" onText="On" offText="Off" 
            onChange={this.handleNoFixedHeight}
            defaultChecked={this.state.noFixedHeight}
          />
          <Toggle label="Hide title (enable if slideInBottom = true)" onText="On" offText="Off" 
            onChange={this.handleSlideInBottomNoTitle}
            defaultChecked={this.state.slideInBottomNoTitle}
          />
          <Toggle label="Enable shimmer" onText="On" offText="Off" 
            onChange={this.handleIsShimmer}
            defaultChecked={this.state.isShimmer}
          />
          <Slider
            label="Board height"
            min={100}
            max={500}
            step={10}
            defaultValue={this.state.boardHeight}
            showValue={true}
            onChange={(value: number) => {this.setState({boardHeight: value})}}
          />
          <Slider
            label="Blog items count"
            min={0}
            max={5}
            step={1}
            defaultValue={this.state.numberOfItems}
            showValue={true}
            onChange={(value: number) => {this.setState({numberOfItems: value})}}
          />
          <div style={{height: 20}}></div>
          <BlogTileBoard 
            items={items}
            mainTile={mainTileProps}
            smallTile={{
              ...mainTileProps,
              maxWidth: mainTileProps.maxWidth as number / 2
            }}
            boardHeight={this.state.boardHeight}
            isShimmer={this.state.isShimmer}
            onClick={this.handleOnClick}
            titleForComments="Number of comments"
            titleForDate="Blog created date"
            titleForLikes="Number of likes"
            titleForLink="Go to the blog..."
            tilePadding={4}
          />
          <div style={{backgroundColor: 'grey', color: 'white', textAlign: 'center'}}>Test padding</div>
      </div>
    );
  }

  private handleIsShimmer = (event: React.MouseEvent<HTMLElement, MouseEvent>, checked?: boolean | undefined) => {
    this.setState({isShimmer: checked});
  }

  private handleOnClick = (data: IBlogTileData) => {
    console.log('click on blog', data);
  }

  private handleHideFooter = (event: React.MouseEvent<HTMLElement, MouseEvent>, checked?: boolean | undefined) => {
    this.setState({hideFooter: checked});
  }

  private handleNoFixedHeight = (event: React.MouseEvent<HTMLElement, MouseEvent>, checked?: boolean | undefined) => {
    this.setState({noFixedHeight: checked});
  }

  private handleNoImage = (event: React.MouseEvent<HTMLElement, MouseEvent>, checked?: boolean | undefined) => {
    this.setState({noImage: checked});
  }

  private handleScaleImage = (event: React.MouseEvent<HTMLElement, MouseEvent>, checked?: boolean | undefined) => {
    this.setState({scaleImageOnHover: checked});
  }

  private handleSlideInBottom = (event: React.MouseEvent<HTMLElement, MouseEvent>, checked?: boolean | undefined) => {
    this.setState({slideInBottom: checked});
  }

  private handleSlideInBottomNoTitle = (event: React.MouseEvent<HTMLElement, MouseEvent>, checked?: boolean | undefined) => {
    this.setState({slideInBottomNoTitle: checked});
  }
}
```


### IBlogTileBoardProps

| Property Name | Required | Type | Comments |
|-|-|-|-|
 | boardHeight |  |  *number* |     Board height       |  
 | className | `Optional` |  *string* |     Add custom class to component       |  
 | isShimmer | `Optional` |  *boolean* |     Enable shimmer mode       |  
 | items |  |  *IBlogTileData[]* |     Tile metadata       |  
 | mainTile |  |  *IBlogTileBaseProps* |     Blog tile base props for main (large) tile       |  
 | onClick | `Optional` |  *function* |     Set custom behavior       |  
 | smallTile |  |  *IBlogTileBaseProps* |     Blog tile base props for small tiles       |  
 | style | `Optional` |  *CSSProperties* |     Add custom standard styles to component       |  
 | tilePadding | `Optional` |  *number* |     Set space between tiles       |  
 | titleForComments | `Optional` |  *string* |     Define title property for comment icon       |  
 | titleForDate | `Optional` |  *string* |     Define title property for blog date       |  
 | titleForLikes | `Optional` |  *string* |     Define title property for like icon       |  
 | titleForLink | `Optional` |  *string* |     Define title property for data block       |
