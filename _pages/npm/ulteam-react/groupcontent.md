---
title: ulteam-react GroupContent
permalink: /npm/ulteam-react/groupcontent/
---

## GroupContent component

Component for expand and collapse content. Just wrap your JSX elements.

### Sample

```js
import * as React from 'react';
import { GroupContent } from '../../../../common/components/GroupContent/GroupContent';

export class TestGroupContent extends React.Component<{}> {
  public render() {
    return (
      <GroupContent expand={true} groupText="My Group Content">
        <p>
          Lorem ipsum dolor sit amet, consectetur adipiscing elit. 
          Morbi faucibus enim a consectetur mollis. 
          In imperdiet venenatis urna, ut tempor augue sagittis quis. 
          Nullam faucibus, sapien eget rutrum vehicula, 
          ligula ex malesuada massa, eu congue turpis magna scelerisque metus. 
          Sed gravida bibendum varius. 
          Vivamus sed lorem dictum dolor volutpat maximus lacinia et enim. 
          Praesent finibus, felis in consectetur sagittis, est est auctor ipsum,
          eu mollis orci dolor sit amet ligula. Pellentesque aliquet massa nulla, 
          et pulvinar massa cursus ac. Nulla in mollis libero. 
          Etiam at libero eu leo suscipit lacinia a at ligula. 
          Quisque vel urna vehicula, efficitur sem non, convallis diam. 
          Donec dictum vitae tortor non ullamcorper.
        </p>
      </GroupContent>
    );
  }
}
```


### IGroupContentProps

| Property Name | Required | Type | Comments |
|-|-|-|-|
 | className | `Optional` |  *string* |     Custom class added to root div of component       |  
 | expand |  |  *boolean* |     Whether expanded block or collapsed       |  
 | groupKey | `Optional` |  *any* |     This key will be pushed to onClick event       |  
 | groupText |  |  *string* |     Group label       |  
 | onClick | `Optional` |  *function* |     Set custom behavior       |
