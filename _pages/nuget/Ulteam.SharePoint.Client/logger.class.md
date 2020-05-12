---
title: Ulteam.SharePoint.Client 
permalink: /nuget/Ulteam.SharePoint.Client/logger/
sidebar:
  nav: "nuget"
---

### Logger Class
Namespace: Ulteam.SharePoint.Client

#### Description
Класс для логирования в список (по умолчанию LogList) текущего сайта.


#### Methods

| Name | Description |
|-|-|
| AddLogItem(ClientContext Context, String ItemId, String Title, String Description, String LogListTitle, Boolean AlwaysNewItem) | Добавление записи в лог.             Список логирования создается автоматически.  <br> **Context**: *SharePoint site collection context.*  <br> **ItemId**: *ID элемента списка.*  <br> **Title**: *Название.*  <br> **Description**: *Описание.*  <br> **LogListTitle**: *Название списка логирования. Значение по умолчанию: "LogList".*  <br> **AlwaysNewItem**: *Всегда создается новый элемент списка, даже если существует элемент с таким же ItemId и Title.             Значение по умолчанию: true.*  |
| GetLogList(ClientContext Context, String ListTitle) | Получение списка логирования.             Создание списка, если он не существует.  <br> **Context**: *SharePoint site collection context.*  <br> **ListTitle**: *Название списка.*  |

#### Samples
```csharp

/// <summary>
/// Добавление записи в лог.
/// </summary>
public void AddLog()
{
    ClientContext context = TestSettings.Context;

    // Добавляет элемент в список LogList.
    // Если список LogList не создан, то создает его.
    Logger.AddLogItem(context, "1", "Log title", "Log description");
    
    // Добавляет элемент в список InfoLogList.
    // Если список InfoLogList не создан, то создает его.
    Logger.AddLogItem(context, "1", "Log title", "Log description", "InfoLogList");
}
```
