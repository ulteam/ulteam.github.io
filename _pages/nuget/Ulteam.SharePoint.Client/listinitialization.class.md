---
title: Ulteam.SharePoint.Client 
permalink: /nuget/Ulteam.SharePoint.Client/listinitialization/
sidebar:
  nav: "nuget"
---

### ListInitialization Class
Namespace: Ulteam.SharePoint.Client

#### Description
Создание списков для работы с процессом.

#### Constructors

| Name | Description |
|-|-|
| ListInitialization() | Инициирование пустого SchemeList.  |

#### Methods

| Name | Description |
|-|-|
| AddLists(ClientContext Context, Boolean AddSamplesToLists) | Добавление списков из SchemeList, если они не существуют.  <br> **Context**: *SharePoint site collection context.*  <br> **AddSamplesToLists**: *Добавить примеры в списки настроек.*  |
| SetByDefault() | Определяем списки по умолчанию.  |

#### Samples
```csharp

/// <summary>
/// Создание списков для процесса и уведомлений
/// </summary>
public void AddStandardLists()
{
    ClientContext context = TestSettings.Context;
    
    // инициирование объекта
    ListInitialization listInitialization = new ListInitialization();

    // добавление схем стандартных список для процессов и уведомлений
    listInitialization.SetByDefault();

    // Можно удалить часть списков, если они не нужны,
    // либо добавить свои списки.
    // Для этого необходимо поменять listInitialization.SchemeList, 
    // как это делается в listInitialization.SetByDefault
    // ------------------------------------------------------------

    // создание списков из listInitialization.SchemeList
    listInitialization.AddLists(context);
}
```
