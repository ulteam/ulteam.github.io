---
title: generator-ulteam-sp
permalink: /npm/generator-ulteam-sp/about/
breadcrumbs: true
search: true
search_full_content: true
---

### Yeoman generator for SharePoint
We have written TypeScript templates for SharePoint classic.

### Install
Install Yeoman and ulteam-sp generator:

```bash
npm install -g yo generator-ulteam-sp
```

### Update
Update generator to latest version:

```bash
npm install -g generator-ulteam-sp@latest
```

### Run

The Yeoman generator will walk you through the steps required to create your customization or extension prompting for the required information.

To launch the generator simply type:

```bash
yo ulteam-sp
```

### Templates

| Name | Description |
|-|-|
| Typescript | Blank typescript template |
| React empty app | React project with only JS + CSS bundle |
| React + Redux empty app | React empty app template with Redux store |
| Grid web part on React | React project with GridWebPart component for ulteam-grid |
| Grid web parts on React in one project | Optimization project with multiple web parts for ulteam-grid |

### Add new web part

In existing project type command below for add new web part
```bash
yo ulteam-sp --add
```