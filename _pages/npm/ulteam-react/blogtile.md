---
title: ulteam-react BlogTile
permalink: /npm/ulteam-react/blogtile/
---

## BlogTile component

Tile with info about News/blog.

### Sample

```js
import * as React from 'react';
import { BlogTile } from '../../../../common/components/BlogTile/BlogTile';
import { IBlogTileData } from '../../../../common/components/BlogTile/BlogTile.types';
import { Toggle } from 'office-ui-fabric-react/lib/components/Toggle/Toggle';

interface ITestState {
  hideFooter?: boolean;

  isShimmer?: boolean;

  noFixedHeight?: boolean;

  noImage?: boolean;

  scaleImageOnHover?: boolean;

  slideInBottom?: boolean;

  slideInBottomNoTitle?: boolean;
}

/**
 * Debug common components
 */
export class TestBlogTile extends React.Component<{}, ITestState> {
  constructor(props: {}) {
    super(props);

    this.state = {
      hideFooter: false,
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
          <div style={{height: 20}}></div>
          <BlogTile 
            data={blogTileData}
            descriptionMaxSize={200}
            tileHeight={250}
            hideFooter={this.state.hideFooter}
            isShimmer={this.state.isShimmer}
            maxWidth={500}
            noFixedDataHeight={this.state.noFixedHeight}
            onClick={this.handleOnClick}
            scaleImageOnHover={this.state.scaleImageOnHover}
            slideInBottom={this.state.slideInBottom}
            slideInBottomNoTitle={this.state.slideInBottomNoTitle}
            titleForComments="Number of comments"
            titleForDate="Blog created date"
            titleForLikes="Number of likes"
            titleForLink="Go to the blog..."
          />
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


### IBlogTileProps

| Property Name | Required | Type | Comments |
|-|-|-|-|
 | className | `Optional` |  *string* |     Add custom class to component       |  
 | commentsIconName | `Optional` |  *string* |     Define your office-ui-fabric-react icon name for comments       |  
 | data | `Optional` |  *IBlogTileData* |     Tile metadata       |  
 | descriptionMaxSize | `Optional` |  *number* |     Description max symbol number       |  
 | hideFooter | `Optional` |  *boolean* |     Whether hide footer (comments, likes, date) or not       |  
 | isShimmer | `Optional` |  *boolean* |     Enable shimmer mode       |  
 | likesIconName | `Optional` |  *string* |     Define your office-ui-fabric-react icon name for likes       |  
 | maxWidth |  |  *number \| string* |     Tile max width (if value is string then add 'px' or '%' to the end)       |  
 | noFixedDataHeight | `Optional` |  *boolean* |     Whether blog data fixex or not This prop enable only if hideFooter = true       |  
 | onClick | `Optional` |  *function* |     Set custom behavior       |  
 | scaleImageOnHover | `Optional` |  *boolean* |     Add scale animation to tile image       |  
 | slideInBottom | `Optional` |  *boolean* |     Add slide-in-bottom animation to blog data       |  
 | slideInBottomNoTitle | `Optional` |  *boolean* |     Whether hide blog title or not if slideInBottom = true       |  
 | style | `Optional` |  *CSSProperties* |     Add custom standard styles to component       |  
 | tileHeight |  |  *number \| string* |     Tile height (if value is string then add 'px' or '%' to the end)       |  
 | titleForComments | `Optional` |  *string* |     Define title property for comment icon       |  
 | titleForDate | `Optional` |  *string* |     Define title property for blog date       |  
 | titleForLikes | `Optional` |  *string* |     Define title property for like icon       |  
 | titleForLink | `Optional` |  *string* |     Define title property for data block       |  
 | titleMaxSize | `Optional` |  *number* |     Blog title max symbol number       |
