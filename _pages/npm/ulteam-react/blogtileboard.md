---
title: ulteam-react BlogTileBoard
permalink: /npm/ulteam-react/blogtileboard/
---

## BlogTileBoard component

Blogs board based on BlogTile component.

### Sample

```js
import * as React from 'react';
import { IBlogTileData } from '../../../../common/components/BlogTile/BlogTile.types';
import { BlogTileBoard } from '../../../../common/components/BlogTileBoard/BlogTileBoard';
import { Slider } from 'office-ui-fabric-react/lib/components/Slider/Slider';
import { TestBlogTileSettings, ITestBlogTileSettingsProps } from '../TestBlogTile/TestBlogTileSettings';

interface ITestState {
  mainTileProps: ITestBlogTileSettingsProps;
  smallTileProps: ITestBlogTileSettingsProps;

  boardHeight: number;

  // hideFooter?: boolean;

  // isShimmer?: boolean;

  // noFixedHeight?: boolean;

  // noImage?: boolean;

  numberOfItems: number;

  // scaleImageOnHover?: boolean;

  // slideInBottom?: boolean;

  // slideInBottomNoTitle?: boolean;
}

/**
 * Debug common components
 */
export class TestBlogTileBoard extends React.Component<{}, ITestState> {
  constructor(props: {}) {
    super(props);

    const mainTileProps: ITestBlogTileSettingsProps = {
      maxWidth: 500,
      titleMaxSize: 200,
      descriptionMaxSize: 200,
      label: "Main tile props",
      onChange: this.handleMainTileProps
    };

    const smallTileProps: ITestBlogTileSettingsProps = {
      maxWidth: 250,
      titleMaxSize: 200,
      descriptionMaxSize: 200,
      label: "Small tile props",
      onChange: this.handleSmallTileProps
    }

    this.state = {
      boardHeight: 250,
      // hideFooter: false,
      mainTileProps,
      numberOfItems: 3,
      smallTileProps
      // scaleImageOnHover: undefined
    };
  }

  public render() {
    const blogTileData: IBlogTileData = {
      title: 'Awesome blog tile title',
      date: '14:57 | 20.06.2020',
      description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi faucibus enim a consectetur mollis. In imperdiet venenatis urna, ut tempor augue sagittis quis. Nullam faucibus, sapien eget rutrum vehicula, ligula ex malesuada massa, eu congue turpis magna scelerisque metus. Sed gravida bibendum varius. Vivamus sed lorem dictum dolor volutpat maximus lacinia et enim. Praesent finibus, felis in consectetur sagittis, est est auctor ipsum, eu mollis orci dolor sit amet ligula. Pellentesque aliquet massa nulla, et pulvinar massa cursus ac. Nulla in mollis libero. Etiam at libero eu leo suscipit lacinia a at ligula. Quisque vel urna vehicula, efficitur sem non, convallis diam. Donec dictum vitae tortor non ullamcorper.',
      imageUrl: this.state.mainTileProps.noImage !== true ? 'https://i.picsum.photos/id/866/1920/1080.jpg' : undefined,
      numberOfComments: 5,
      numberOfLikes: 6
    }

    const items: IBlogTileData[] = [];
    for (let i = 0; i < this.state.numberOfItems; i++) {
      items.push({...blogTileData});
    }

    return (
      <div>
          <h3>BlogTile component</h3>
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
          <div style={{ display: 'flex' }}>
            <TestBlogTileSettings
              {...this.state.mainTileProps}
            />
            <TestBlogTileSettings
              {...this.state.smallTileProps}
            />
          </div>
          <div style={{height: 20}}></div>
          <BlogTileBoard 
            items={items}
            mainTile={this.state.mainTileProps}
            smallTile={this.state.smallTileProps}
            boardHeight={this.state.boardHeight}
            isShimmer={this.state.mainTileProps.isShimmer}
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

  private handleMainTileProps = (props: ITestBlogTileSettingsProps) => {
    this.setState({
      mainTileProps: {
        ...props
      }
    });
  }

  private handleSmallTileProps = (props: ITestBlogTileSettingsProps) => {
    this.setState({
      smallTileProps: {
        ...props
      }
    });
  }

  private handleOnClick = (data: IBlogTileData) => {
    console.log('click on blog', data);
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
