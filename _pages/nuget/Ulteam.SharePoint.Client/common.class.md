---
title: Ulteam.SharePoint.Client 
permalink: /nuget/Ulteam.SharePoint.Client/common/
sidebar:
  nav: "nuget"
---

### Common Class
Namespace: Ulteam.SharePoint.Client

#### Description
Общие методы по работе с CSOM.


#### Methods

| Name | Description |
|-|-|
| GetClientContext(String WebFullUrl, String Login, String Password) | Получение ClientContext.  <br> **WebFullUrl**: *Полный URL до узла.*  <br> **Login**: *Логин учетной записи.*  <br> **Password**: *Пароль учетной записи.*  |
| GetServerUrl(String AbsoluteUrl) | Получение ServerUrl из AbsoluteUrl = {serverUrl}/{siteCollection}/{web}.  <br> **AbsoluteUrl**: *Полный путь, начиная с http или https.*  |

#### Samples
```csharp

public void GetServerUrl()
{
    // Проверка Office 365
    string url = "https://tenantName.sharepoint.com/sites/webname";
    string serverUrl = Common.GetServerUrl(url); // вернется "https://tenantName.sharepoint.com"

    // Проверка SharePoint Server
    url = "http://serverName/sites/webname";
    serverUrl = Common.GetServerUrl(url); // вернется "http://serverName"

    // Проверка относительной ссылки
    url = "/sites/webname";
    serverUrl = Common.GetServerUrl(url); // вернется ""
}
```
```csharp

private void GetClientContext()
{
    ClientContext context = Common.GetClientContext(
        "https://tenantName.sharepoint.com/sites/webname",
        "login@sample.com",
        "***");
}
```
