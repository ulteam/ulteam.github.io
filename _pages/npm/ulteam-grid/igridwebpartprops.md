---
title: ulteam-grid GridWebPart
permalink: /npm/ulteam-grid/gridwebpart/
---

# Interface: IGridWebPartProps

## GridWebPart component
Web part for UlteamGrid component. Component handle web part properties, add wrap for page on edit mode (edit, delete icons, property panel for change properties).
### IGridWebPartProps

| Property Name | Required | Type | Comments |
|-|-|-|-|
 | config | `Optional` |  *IPropertyConfig* |     Property Panel configuration       |  
 | customSPContext | `Optional` |  *ICustomSPContext* |     Custom SharePoint context (all needed props from _spPageContextInfo) Use for localhost or without SharePoint.       |  
 | editorMode |  |  *boolean* |     Page on edit mode       |  
 | handleProperties |  |  *function* |     Property update handle       |  
 | noRestApi | `Optional` |  *boolean* |     If value is true then you can use your own API instead of SharePoint REST API.       |  
 | onAction | `Optional` |  *function* |     If noRestApi = true, you can add your own API and handle any action.       |  
 | toolbarBtnSize | `Optional` |  *number* |     Button edit, delete size in px. Default: 32px       |  
 | webPartConfig |  |  *IWebPartConfig‹any›* |  |  
 | webPartId |  |  *number* |     GridZoneWebParts list item id       |
