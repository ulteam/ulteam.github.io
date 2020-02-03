---
title: ulteam-grid UlteamGrid
permalink: /npm/ulteam-grid/ulteamgrid/
---

# Interface: IUlteamGridProps

## UlteamGrid component
UlteamGrid is a component that allows you to manage your page in style aka SharePoint Modern Page style.
You can:
- add web part zones
- configure your own web part catalog
- add your GridWebPart's
- store web part properties
### IUlteamGridProps

| Property Name | Required | Type | Comments |
|-|-|-|-|
 | configListUrl |  |  *string* |     GridConfig list root folder url       |  
 | customSPContext | `Optional` |  *ICustomSPContext* |     Custom SharePoint context (all needed props from _spPageContextInfo) Use for localhost or without SharePoint.       |  
 | noRestApi | `Optional` |  *boolean* |     If value is true then you can use your own API instead of SharePoint REST API.       |  
 | onAction | `Optional` |  *function* |     If noRestApi = true, you can add your own API and handle any action.       |  
 | settingWebUrl |  |  *string* |     GridConfig web base url (without sitecollection)       |
