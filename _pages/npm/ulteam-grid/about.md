---
title: ulteam-grid
permalink: /npm/ulteam-grid/about/
breadcrumbs: true
search: true
search_full_content: true
---

#### React TypeScript components for Grid Web Parts

React components for setting SharePoint "Grid Web Parts" like SharePoint Framework web parts. 
Managing web parts working on [@pnp/sp](https://pnp.github.io/pnpjs/sp/) by default.
If you want to use your own API, just add noRestApi & onAction props to your UlteamGrid component.
Components based on [Office UI Fabric React](https://www.npmjs.com/package/office-ui-fabric-react) library.

#### Components

| Name | Description |
|-|-|
| [UlteamGrid](/npm/ulteam-grid/ulteamgrid/) | There is a bootstrap of grid web part page. |
| [GridWebPart](/npm/ulteam-grid/gridwebpart/) | There is a bootstrap of grid web part page. |

#### Getting Started

- Create your grid page with UlteamGrid component.

- Create your web part using [generator-ulteam-sp](https://www.npmjs.com/package/generator-ulteam-sp) Grid web part template.

#### Property Panel

You can configure Property Panel like SPFx web part Property Panel.

#### Property Panel Field Types

Add needed properties like this:

- Text field

```js
Properties.TextField('title', {
  label: 'Title',
  required: true,
  description: 'Web part header text',
  errorMessage: 'Required field!!!',
  value: this.state.properties.title
})
```

- Boolean field

```js
Properties.BooleanField('booleanField', {
  label: 'your confirmation',
  value: this.state.properties.booleanField
})
```

- Choice field

```js
Properties.ChoiceField('choiceField', {
  label: 'Choice',
  value: this.state.properties.choiceField,
  required: true,
  errorMessage: 'Required field!!!',
  placeholder: 'Select a value',
  options: [
    {
      key: 'Key 1',
      text: 'Text 1'
    },
    {
      key: 'Key 2',
      text: 'Text 2'
    },
    {
      key: 'Key 3',
      text: 'Text 3'
    }
  ]
})
```

- List field

```js
Properties.ListField('listField', {
  value: this.state.properties.listField,
  config: {
    label: 'Test list',
    panelType: PanelType.medium,
    panelHeader: 'Test list',
    panelDescription: 'Description',
    fields: [
      UListProperties.TextField('Title', {
        label: 'Title label',
        defaultValue: 'Default value',
        required: true,
        description: 'test label description',
        errorMessage: 'Required field!!!',
        flexGrow: 2
      }),
      UListProperties.TextField('Name', {
        label: 'Name label',
        required: true,
        description: 'name label description',
        errorMessage: 'Name value is required!!!'
      }),
      UListProperties.BooleanField('ListBoolean', {
        label: 'List check',
        defaultValue: false
      }),
      UListProperties.ChoiceField('ListChoice', {
        label: 'Choice label',
        defaultValue: 'key 2',
        required: true,
        description: 'email label description',
        errorMessage: 'email value is required!!!',
        options: [
          {
            key: 'key 1',
            text: 'Choice 1'
          },
          {
            key: 'key 2',
            text: 'Choice 2'
          },
          {
            key: 'key 3',
            text: 'Choice 3'
          }
        ]
      })
    ]
  }
})
```