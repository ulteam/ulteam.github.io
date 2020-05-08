---
title: Ulteam.SharePoint 
permalink: /nuget/Ulteam.SharePoint/logger/
sidebar:
  nav: "nuget"
---

### Logger Class
Namespace: Ulteam.SharePoint

#### Description
Класс для логирования в список (по умолчанию LogList) текущего сайта.


#### Methods

| Name | Description |
|-|-|
| AddLogItem(SPWeb Web, String ItemId, String Title, String Description, String LogListUrl, Boolean AlwaysNewItem) | Добавление записи в лог.             Список логирования создается автоматически.  <br> **Web**: *Узел с логами.*  <br> **ItemId**: *ID элемента списка.*  <br> **Title**: *Название.*  <br> **Description**: *Описание.*  <br> **LogListUrl**: *Url списка логирования, после web server relative url. Значение по умолчанию: "/Lists/LogList".*  <br> **AlwaysNewItem**: *Всегда создается новый элемент списка, даже если существует элемент с таким же ItemId и Title. Значение по умолчанию: true.*  |

#### Samples
```csharp

public void AddLog()
{
    SPWeb web = Settings.Mock.Web;

    // Добавляет элемент в список LogList.
    // Если список LogList не создан, то создает его.
    web.AddLogItem("1", "Log title", "Log description");
    web.AddLogItem("2", "Log title 2", "Log description 2");

    // Добавляет элемент в список InfoLogList.
    // Если список InfoLogList не создан, то создает его.
    web.AddLogItem("1", "Log title", "Log description", "InfoLogList");
}
```
