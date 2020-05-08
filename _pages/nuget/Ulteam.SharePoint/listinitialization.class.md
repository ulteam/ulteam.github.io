---
title: Ulteam.SharePoint 
permalink: /nuget/Ulteam.SharePoint/listinitialization/
sidebar:
  nav: "nuget"
---

### ListInitialization Class
Namespace: Ulteam.SharePoint

#### Description
Создание списков для работы с процессом.

#### Constructors

| Name | Description |
|-|-|
| ListInitialization() | Инициирование пустого SchemeList.  |

#### Methods

| Name | Description |
|-|-|
| AddLists(SPWeb Web, Boolean AddSamplesToLists) | Добавление списков из SchemeList, если они не существуют.  <br> **Web**: *Узел для создания на нем списков.*  <br> **AddSamplesToLists**: *Добавить примеры в списки настроек.*  |
| SetByDefault() | Определяем списки по умолчанию.  |

#### Samples
```csharp

public void AddStandardLists()
{
    SPWeb web = Settings.Mock.Web;
    
    // инициирование объекта
    ListInitialization listInitialization = new ListInitialization();

    // добавление схем стандартных список для процессов и уведомлений
    listInitialization.SetByDefault();

    // Можно удалить часть списков, если они не нужны,
    // либо добавить свои списки.
    // Для этого необходимо поменять listInitialization.SchemaList, 
    // как это делается в listInitialization.SetByDefault
    // ------------------------------------------------------------

    // создание списков из listInitialization.SchemaList
    listInitialization.AddLists(web);
}
```
