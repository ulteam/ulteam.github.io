---
title: Ulteam.SharePoint.Client 
permalink: /nuget/Ulteam.SharePoint.Client/permissions/
sidebar:
  nav: "nuget"
---

### Permissions Class
Namespace: Ulteam.SharePoint.Client

#### Description
Класс по работе с правами на элементе списка SharePoint


#### Methods

| Name | Description |
|-|-|
| AddRoleAssignment(ClientContext Context, ListItem Item, Principal Principal, RoleDefinition RoleDefinition, Boolean ExecuteQuery) | Добавляет права пользователю или группе Principal на элемент списка Item.  <br> **Context**: *SharePoint site collection context*  <br> **Item**: *Элемент списка*  <br> **Principal**: *Пользователь или группа*  <br> **RoleDefinition**: *Определение роли*  <br> **ExecuteQuery**: *Если true, то выполняется Context.ExecuteQuery(). Значение по умолчанию: true.*  |
| AddRoleAssignment(ClientContext Context, ListItem Item, Principal Principal, String RoleDefinitionName, Boolean ExecuteQuery) | Добавляет права пользователю или группе Principal на элемент списка Item.  <br> **Context**: *SharePoint site collection context*  <br> **Item**: *Элемент списка*  <br> **Principal**: *Пользователь или группа*  <br> **RoleDefinitionName**: *Название роли. Например: "Совместная работа", "Чтение" и т.д.*  <br> **ExecuteQuery**: *Если true, то выполняется Context.ExecuteQuery(). Значение по умолчанию: true.*  |
| ChangeRoleAssignment(ClientContext Context, ListItem Item, Principal Principal, String DeleteRoleDefinitionName, String AddRoleDefinitionName) | Замена прав пользователя или группы Principal на элемент списка Item.  <br> **Context**: *SharePoint site collection context*  <br> **Item**: *Элемент списка*  <br> **Principal**: *Пользователь или группа*  <br> **DeleteRoleDefinitionName**: *Название роли для удаления. Например: "Совместная работа", "Чтение" и т.д.*  <br> **AddRoleDefinitionName**: *Название роли для добавления. Например: "Совместная работа", "Чтение" и т.д.*  |
| ChangeRoleAssignment(ClientContext Context, ListItem Item, Principal Principal, RoleDefinition DeleteRoleDefinition, RoleDefinition AddRoleDefinition) | Замена прав пользователя или группы Principal на элемент списка Item.  <br> **Context**: *SharePoint site collection context*  <br> **Item**: *Элемент списка*  <br> **Principal**: *Пользователь или группа*  <br> **DeleteRoleDefinition**: *Определение роли для удаления. Например: "Совместная работа", "Чтение" и т.д.*  <br> **AddRoleDefinition**: *Определение роли для добавления. Например: "Совместная работа", "Чтение" и т.д.*  |
| ContainsRoleDefinition(RoleDefinitionBindingCollection RoleDefinitionBindings, RoleDefinition RoleDefinition) | Определяет вхождение роли в коллекцию.  <br> **RoleDefinitionBindings**: *Коллекция ролей*  <br> **RoleDefinition**: *Определение роли*  |
| GetRoleAssignment(ClientContext Context, ListItem Item, Principal Principal) | Получение установленных прав пользователя или группы Principal на элемент списка Item.  <br> **Context**: *SharePoint site collection context*  <br> **Item**: *Элемент списка*  <br> **Principal**: *Пользователь или группа*  |
| GetRoleAssignmentContext(ClientContext Context, RoleAssignment RoleAssignment, Boolean ExecuteQuery) | Получение Member (пользователь или группа) и RoleDefinitionBindings (коллекция ролей) для RoleAssignment  <br> **Context**: *SharePoint site collection context*  <br> **RoleAssignment**: *Установленные права пользователя или группы*  <br> **ExecuteQuery**: *Если true, то выполняется Context.ExecuteQuery(). Значение по умолчанию: true.*  |
| GetRoleAssignmentCollection(ClientContext Context, ListItem Item, Boolean ExecuteQuery) | Получение всех установленных прав на элемент списка Item  <br> **Context**: *SharePoint site collection context*  <br> **Item**: *Элемент списка*  <br> **ExecuteQuery**: *Если true, то выполняется Context.ExecuteQuery(). Значение по умолчанию: true.*  |
| GetPrincipals(ClientContext Context, ListItem Item, Boolean ExceptRestrictedRead) | Получение всех Principal'ов у элемента списка Item.  <br> **Context**: *SharePoint site collection context*  <br> **Item**: *Элемент списка*  <br> **ExceptRestrictedRead**: *Если true, то не учитываются Principal'ы только с уровнем разрешений "Ограниченный доступ" (или "Restricted Read" для англоязычных сайтов).              Значение по умолчанию: true*  |
| GetPrincipalsExceptList(ClientContext Context, ListItem Item, List&lt;String&gt; ExceptRoleDefinitionNameList, Boolean ExceptRestrictedRead) | Получение всех Principal'ов у элемента списка Item.             Не учитываются Principal'ы, у которых есть права только из списка ExceptRoleDefinitionNameList  <br> **Context**: *SharePoint site collection context*  <br> **Item**: *Элемент списка*  <br> **ExceptRoleDefinitionNameList**: *Список названий уровней разрешений, которые необходимо игнорировать.*  <br> **ExceptRestrictedRead**: *Если true, то не учитываются Principal'ы только с уровнем разрешений "Ограниченный доступ" (или "Restricted Read" для англоязычных сайтов).              Значение по умолчанию: true*  |
| GetRoleAssignmentsExceptList(ClientContext Context, ListItem Item, List&lt;String&gt; ExceptRoleDefinitionNameList) | Получение всех установленных прав на элемент списка Item.             Не учитываются RoleAssignment'ы, у которых есть RoleDefinition.Name только из списка ExceptRoleDefinitionNameList  <br> **Context**: *SharePoint site collection context*  <br> **Item**: *Элемент списка*  <br> **ExceptRoleDefinitionNameList**: *Список названий уровней разрешений, которые необходимо игнорировать.*  |
| GetRoleDefinition(ClientContext Context, String RoleName, Boolean ExecuteQuery) | Получение RoleDefinition по названию роли.  <br> **Context**: *SharePoint site collection context*  <br> **RoleName**: *Название роли. Возможные значения: Совместная работа, Изменение, Чтение и т.д.*  <br> **ExecuteQuery**: *Если true, то выполняется Context.ExecuteQuery(). Значение по умолчанию: true.*  |
| GetRoleDefinition(ClientContext Context, RoleType RoleType, Boolean ExecuteQuery) | Получение RoleDefinition по типу стандартной роли.  <br> **Context**: *SharePoint site collection context*  <br> **RoleType**: *Тип стандартной роли*  <br> **ExecuteQuery**: *Если true, то выполняется Context.ExecuteQuery(). Значение по умолчанию: true.*  |
| DeleteRoleDefinitionBinding(RoleAssignment RoleAssignment, RoleDefinition RoleDefinition) | Удаление роли RoleDefinition из коллекции ролей RoleDefinitionBindings для установленных прав RoleAssignment на элемент списка.             Для сохранения изменений необходим Context.ExecuteQuery().  <br> **RoleAssignment**: *Установленные права на элемент списка*  <br> **RoleDefinition**: *Роль для удаления*  |
| DeletePermissionsByRoleDefinition(ClientContext Context, ListItem Item, RoleDefinition RoleDefinition, Boolean ExecuteQuery) | Удаление всех прав определенной роли RoleDefinition из элемента списка Item  <br> **Context**: *SharePoint site collection context*  <br> **Item**: *Элемент списка*  <br> **RoleDefinition**: *Роль для удаления*  <br> **ExecuteQuery**: *Если true, то выполняется Context.ExecuteQuery(). Значение по умолчанию: true.*  |
| DeletePermissionsByRoleTitle(ClientContext Context, ListItem Item, String RoleTitle, Boolean ExecuteQuery) | Удаление всех прав определенного типа RoleTitle из элемента списка Item  <br> **Context**: *SharePoint site collection context*  <br> **Item**: *Элемент списка*  <br> **RoleTitle**: *Название роли (в уровнях разрешений site collection) для удаления. Возможные значения: Совместная работа, Изменение, Чтение и т.д.*  <br> **ExecuteQuery**: *Если true, то выполняется Context.ExecuteQuery(). Значение по умолчанию: true.*  |
| DeletePermissionsByRoleType(ClientContext Context, ListItem Item, RoleType RoleType, Boolean ExecuteQuery) | Удаление всех прав определенного типа RoleType из элемента списка Item  <br> **Context**: *SharePoint site collection context*  <br> **Item**: *Элемент списка*  <br> **RoleType**: *Тип стандартной роли для удаления*  <br> **ExecuteQuery**: *Если true, то выполняется Context.ExecuteQuery(). Значение по умолчанию: true.*  |
| DeletePermissionByRoleDefinition(ClientContext Context, ListItem Item, Principal Principal, RoleDefinition RoleDefinition) | Удаление прав пользователя или группы Principal определенной роли RoleDefinition из элемента списка Item.  <br> **Context**: *SharePoint site collection context*  <br> **Item**: *Элемент списка*  <br> **Principal**: *Пользователь или группа. Параметр может быть следующих типов: Principal, User, Group*  <br> **RoleDefinition**: *Роль для удаления*  |
| DeletePermissionByRoleTitle(ClientContext Context, ListItem Item, Principal Principal, String RoleTitle) | Удаление прав пользователя или группы Principal определенного типа RoleTitle из элемента списка Item  <br> **Context**: *SharePoint site collection context*  <br> **Item**: *Элемент списка*  <br> **Principal**: *Пользователь или группа. Параметр может быть следующих типов: Principal, User, Group*  <br> **RoleTitle**: *Название роли (в уровнях разрешений site collection) для удаления. Возможные значения: Совместная работа, Изменение, Чтение и т.д.*  |
| DeletePermissionByRoleType(ClientContext Context, ListItem Item, Principal Principal, RoleType RoleType) | Удаление прав пользователя или группы Principal определенного типа RoleType из элемента списка Item  <br> **Context**: *SharePoint site collection context*  <br> **Item**: *Элемент списка*  <br> **Principal**: *Пользователь или группа. Параметр может быть следующих типов: Principal, User, Group*  <br> **RoleType**: *Тип стандартной роли для удаления*  |
| DeletePermissions(ClientContext Context, ListItem Item, Principal Principal, Boolean ExceptRestrictedRead, Boolean ExecuteQuery) | Удаление всех прав пользователя или группы Principal из элемента списка Item.  <br> **Context**: *SharePoint site collection context*  <br> **Item**: *Элемент списка*  <br> **Principal**: *Пользователь или группа. Параметр может быть следующих типов: Principal, User, Group*  <br> **ExceptRestrictedRead**: *Если true, то удалятся все уровни разрешений, кроме "Ограниченный доступ" (или "Restricted Read" для англоязычных сайтов).              Значение по умолчанию: true*  <br> **ExecuteQuery**: *Если true, то выполняется Context.ExecuteQuery(). Значение по умолчанию: true.*  |
| DeletePermissionsExceptList(ClientContext Context, ListItem Item, Principal Principal, List&lt;String&gt; ExceptRoleDefinitionNameList, Boolean ExceptRestrictedRead, Boolean ExecuteQuery) | Удаление всех прав пользователя или группы Principal из элемента списка Item, кроме ExceptRoleDefinitionList.  <br> **Context**: *SharePoint site collection context*  <br> **Item**: *Элемент списка*  <br> **Principal**: *Пользователь или группа. Параметр может быть следующих типов: Principal, User, Group*  <br> **ExceptRoleDefinitionNameList**: *Список названий уровней разрешений, которые необходимо оставить.*  <br> **ExceptRestrictedRead**: *Если true, то удалятся все уровни разрешений, кроме "Ограниченный доступ" (или "Restricted Read" для англоязычных сайтов).              Значение по умолчанию: true*  <br> **ExecuteQuery**: *Если true, то выполняется Context.ExecuteQuery(). Значение по умолчанию: true.*  |
| IsEquivalent(Principal Principal, Principal ComparePrincipal) | Сравнение Principal'ов по Title'ам без учета регистра  <br> **Principal**: *Пользователь или группа*  <br> **ComparePrincipal**: *Пользователь или группа*  |

#### Samples
```csharp

public void Init()
{
    ClientContext context = TestSettings.Context;

    List list = TestSettings.PermissionsList;

    Dictionary<string, object> itemData = new Dictionary<string, object>
    {
        { "Title", "AddRoleAssignmentTest1" }
    };
    ListItem item = Lists.AddListItem(context, list, itemData);

    Principal groupPrincipal = context.Web.SiteGroups.GetByName("Unit Tests - посетители");

    // удаление прав определенного типа у пользователя или группы
    DeletePermissionByPrincipal(context, item, groupPrincipal);
    
    // удаление всех прав у пользователя или группы
    DeleteAllPermissionsByPrincipal(context, item, groupPrincipal);
    
    // удаление прав определенного типа у всех пользователей или групп
    DeleteAllPermissions(context, item);
    
    // добавление прав
    AddPermissions(context, item, groupPrincipal);

    // замена одних прав на другие
    ChangePermissions(context, item, groupPrincipal);

    // получение пользователей и групп, имеющих права на список
    List<Principal> principalList = GetPrincipalsExceptList(context, item);

    // настройка прав
    SetPermissions(context, item);

}
```
```csharp

/// <summary>
/// Добавляет права пользователю или группе. 
/// </summary>
private void AddPermissions(ClientContext context, ListItem item, Principal groupPrincipal)
{
    // добавление прав "Совместная работа" группе "Ulteam Site - посетители" на элемент спика item.
    context.AddRoleAssignment(item, groupPrincipal, "Совместная работа");

    // то же самое, только используя RoleDefinition
    RoleDefinition roleDefinition = context.GetRoleDefinition("Совместная работа");
    context.AddRoleAssignment(item, groupPrincipal, roleDefinition);
}
```
```csharp

/// <summary>
/// Замена прав пользователя или группы. 
/// </summary>
private void ChangePermissions(ClientContext context, ListItem item, Principal groupPrincipal)
{
    // замена прав у группы с "Совместная работа" на "Чтение"
    context.ChangeRoleAssignment(item, groupPrincipal, "Совместная работа", "Чтение");

    // то же самое, используя RoleDefinition'ы
    RoleDefinition deleteRoleDefinition = context.GetRoleDefinition("Совместная работа");
    RoleDefinition addRoleDefinition = context.GetRoleDefinition("Чтение");

    context.ChangeRoleAssignment(item, groupPrincipal, deleteRoleDefinition, addRoleDefinition);
}
```
```csharp

/// <summary>
/// Удаление прав определенного типа у всех пользователей или групп. 
/// </summary>
private void DeleteAllPermissions(ClientContext context, ListItem item)
{
    // удаление прав "Совместная работа" у всех пользователей и групп.
    context.DeletePermissionsByRoleTitle(item, "Совместная работа");

    // то же самое, используя RoleDefinition
    RoleDefinition roleDefinition = context.GetRoleDefinition("Совместная работа");
    context.DeletePermissionsByRoleDefinition(item, roleDefinition);

    // то же самое, используя RoleType
    context.DeletePermissionsByRoleType(item, RoleType.Contributor);
}
```
```csharp

/// <summary>
/// Удаление всех прав у пользователя или группы. 
/// </summary>
private void DeleteAllPermissionsByPrincipal(ClientContext context, ListItem item, Principal groupPrincipal)
{
    // удаление всех уровней разрешений для группы, кроме "Ограниченный доступ"
    context.DeletePermissions(item, groupPrincipal);

    List<string> roleDefinitionNameList = new List<string>
    {
        "Чтение",
        "Только просмотр"
    };
     
    // удаление всех уровней разрешений для группы, кроме "Чтение", "Только просмотр" и "Ограниченный доступ"
    context.DeletePermissionsExceptList(item, groupPrincipal, roleDefinitionNameList);
}
```
```csharp

/// <summary>
/// Удаление определенных прав пользователя или группы. 
/// </summary>
private void DeletePermissionByPrincipal(ClientContext context, ListItem item, Principal groupPrincipal)
{
    // удаление прав "Совместная работа" у всех пользователей и групп.
    context.DeletePermissionByRoleTitle(item, groupPrincipal, "Совместная работа");

    // то же самое, используя RoleDefinition
    RoleDefinition roleDefinition = context.GetRoleDefinition("Совместная работа");
    context.DeletePermissionByRoleDefinition(item, groupPrincipal, roleDefinition);

    // то же самое, используя RoleType
    context.DeletePermissionByRoleType(item, groupPrincipal, RoleType.Contributor);
}
```
```csharp

/// <summary>
/// Получение всех пользователей и групп, имеющих права на элемент списка.
/// </summary>
private List<Principal> GetPrincipalsExceptList(ClientContext context, ListItem item)
{
    List<string> roleDefinitionNameList = new List<string>
    {
        "Чтение",
        "Только просмотр"
    };

    // получение всех пользователей и групп, 
    // у которых есть какие-нибудь уровни разрешений на элемент Item, 
    // кроме "Чтение", "Только просмотр" и "Ограниченный доступ"
    return context.GetPrincipalsExceptList(item, roleDefinitionNameList);
}
```
```csharp

/// <summary>
/// В этом примере все права (кроме прав "Полный доступ") у всех пользователей и групп заменяются на права "Чтение".
/// Плюс добавляются отдельно права "Совместная работа" для создателя элемента списка.
/// </summary>
private void SetPermissions(ClientContext context, ListItem item)
{
    FieldUserValue authorValue = item.GetValueAsUser("Author");
    Principal authorPrincipal = context.Site.RootWeb.SiteUsers.GetById(authorValue.LookupId);

    context.Load(authorPrincipal);
    context.ExecuteQuery();

    RoleDefinition editorRoleDefinition = context.GetRoleDefinition("Совместная работа");
    RoleDefinition readerRoleDefinition = context.GetRoleDefinition("Чтение");

    // получаем список всех пользователей и групп с правами, кроме ограниченного доступа
    List<Principal> principalList = context.GetPrincipals(item);

    // добавляем всем права на чтение
    foreach (Principal principal in principalList)
        context.AddRoleAssignment(item, principal, readerRoleDefinition, false);
    context.ExecuteQuery();

    // удаляем права у всех остальных пользователей или групп, кроме прав "Чтение" и "Полный доступ"
    List<string> exceptRoleDefinitionList = new List<string>
    {
        "Чтение",
        "Полный доступ"
    };
    foreach (Principal principal in principalList)
        context.DeletePermissionsExceptList(item, principal, exceptRoleDefinitionList, true, false);
    context.ExecuteQuery();

    // добавляем инициатору отдельные права "Совместная работа"
    context.AddRoleAssignment(item, authorPrincipal, editorRoleDefinition);
}
```
