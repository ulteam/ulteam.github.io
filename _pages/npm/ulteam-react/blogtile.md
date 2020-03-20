---
title: ulteam-react BlogTile
permalink: /npm/ulteam-react/blogtile/
---

## BlogTile component

Tile with info about News/blog.

### Demo
Try component on the [demo](/npm/ulteam-react/demo/?r=blogtile)

### Sample

```tsx
import * as React from 'react';
import { BlogTile } from '../../../../common/components/BlogTile/BlogTile';
import { IBlogTileData } from '../../../../common/components/BlogTile/BlogTile.types';
import { TestBlogTileSettings, ITestBlogTileSettingsProps } from './TestBlogTileSettings';

interface ITestState {
  hideFooter?: boolean;

  isShimmer?: boolean;

  maxWidth: number;

  noFixedHeight?: boolean;

  noImage?: boolean;

  openLinkInNewTab?: boolean;

  scaleImageOnHover?: boolean;

  slideInBottom?: boolean;

  slideInBottomNoTitle?: boolean;

  titleMaxSize?: number;
}

/**
 * Debug common components
 */
export class TestBlogTile extends React.Component<{}, ITestState> {
  constructor(props: {}) {
    super(props);

    this.state = {
      hideFooter: false,
      maxWidth: 500,
      scaleImageOnHover: undefined,
      titleMaxSize: 200
    };
  }

  public render() {
    const blogTileData: IBlogTileData = {
      title: 'Awesome blog tile title',
      date: '14:57 | 20.06.2020',
      description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi faucibus enim a consectetur mollis. In imperdiet venenatis urna, ut tempor augue sagittis quis. Nullam faucibus, sapien eget rutrum vehicula, ligula ex malesuada massa, eu congue turpis magna scelerisque metus. Sed gravida bibendum varius. Vivamus sed lorem dictum dolor volutpat maximus lacinia et enim. Praesent finibus, felis in consectetur sagittis, est est auctor ipsum, eu mollis orci dolor sit amet ligula. Pellentesque aliquet massa nulla, et pulvinar massa cursus ac. Nulla in mollis libero. Etiam at libero eu leo suscipit lacinia a at ligula. Quisque vel urna vehicula, efficitur sem non, convallis diam. Donec dictum vitae tortor non ullamcorper.',
      href: this.state.openLinkInNewTab === true ? 'https://google.com' : undefined,
      imageUrl: this.state.noImage !== true ? 'https://i.picsum.photos/id/866/1920/1080.jpg' : undefined,
      numberOfComments: 5,
      numberOfLikes: 6
    }

    return (
      <div>
          <h3>BlogTile component</h3>
          <TestBlogTileSettings
            {...this.state}
            label="Settings"
            onChange={this.handleSettings}
          />
          <div className="emptyHeight"></div>
          <BlogTile 
            data={blogTileData}
            descriptionMaxSize={200}
            target={this.state.openLinkInNewTab === true ? '_blank' : undefined}
            tileHeight={250}
            onClick={this.handleOnClick}
            titleForComments="Number of comments"
            titleForDate="Blog created date"
            titleForLikes="Number of likes"
            titleForLink="Go to the blog..."
            {...this.state}
          />
      </div>
    );
  }

  private handleSettings = (props: ITestBlogTileSettingsProps) => {
    this.setState({...props});
  }

  private handleOnClick = (data: IBlogTileData) => {
    console.log('click on blog', data);
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
 | target | `Optional` |  *string* |     Standard 'a' tag target attribute for title and description       |  
 | tileHeight |  |  *number \| string* |     Tile height (if value is string then add 'px' or '%' to the end)       |  
 | titleForComments | `Optional` |  *string* |     Define title property for comment icon       |  
 | titleForDate | `Optional` |  *string* |     Define title property for blog date       |  
 | titleForLikes | `Optional` |  *string* |     Define title property for like icon       |  
 | titleForLink | `Optional` |  *string* |     Define title property for data block       |  
 | titleMaxSize | `Optional` |  *number* |     Blog title max symbol number       |
