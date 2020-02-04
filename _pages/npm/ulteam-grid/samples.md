---
title: ulteam-grid Samples
permalink: /npm/ulteam-grid/samples/
---

## UlteamGrid sample 
First you must add UlteamGrid component to your page.
It's sample for localhost:

```js
import * as React from 'react';
import { UlteamGrid, IUlteamGridAction, ADD_ITEM, GET_ITEMS, IUlteamGridActionResult, ICustomSPContext } from 'ulteam-grid/lib/';
import MockData from 'ulteam-grid/lib/data/MockData';

export class TestUlteamGrid extends React.Component<{}, {}> {
  private newItemIdCounter: number = 1;
  public render() {
    const spContext: ICustomSPContext = {
      pageItemId: 1,
      pageListId: '{34ae3621-5833-4f68-babe-8fd2b8abbbdb}',
      siteAbsoluteUrl: 'http://localhost/site',
      siteServerRelativeUrl: '/site'
    }

    return (
      <UlteamGrid 
        // add this if you don't want to use values from _spPageContextInfo object
        // or if you want to use this values for localhost
        customSPContext={spContext}

        // whether use custom API or SharePoint REST API
        noRestApi={true}

        // callback for custom API
        onAction={this.handleOnAction}

        settingWebUrl='ulteamgrid' 
        configListUrl='/Lists/GridConfig'
      />
    );
  }

  /**
   * Here add your own API
   */
  public handleOnAction = async (action: IUlteamGridAction): Promise<IUlteamGridActionResult> => {
    const result: IUlteamGridActionResult = {
      data: {}
    };

    console.log(action);

    switch (action.action.type) {
      case ADD_ITEM:
        result.data = {
          ...action.action.itemData,
          Id: this.newItemIdCounter
        };
        this.newItemIdCounter++;
        break;

      case GET_ITEMS:
        // add your async calling this
        if (action.action.listUrl.indexOf('GridConfig') > -1) {
          result.data = MockData.getConfig();
        }
        if (action.action.listUrl.indexOf('Grids') > -1) {
          result.data = [];
        }
        if (action.action.listUrl.indexOf('GridZones') > -1) {
          result.data = [];
        }
        if (action.action.listUrl.indexOf('GridZoneWebPartCatalog') > -1) {
          result.data = MockData.getCatalogWebParts();
        }
    }

    return result;
  }
}
```