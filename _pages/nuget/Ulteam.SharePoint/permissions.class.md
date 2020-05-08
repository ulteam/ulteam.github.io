---
title: Ulteam.SharePoint 
permalink: /nuget/Ulteam.SharePoint/permissions/
sidebar:
  nav: "nuget"
---

### Permissions Class
Namespace: Ulteam.SharePoint

#### Description
Класс по работе с правами на элементе списка SharePoint


#### Methods

| Name | Description |
|-|-|
| AddRoleAssignment(SPListItem Item, SPPrincipal Principal, SPRoleDefinition RoleDefinition) | Добавляет права пользователю или группе Principal на элемент списка Item.  <br> **Item**: *Элемент списка*  <br> **Principal**: *Пользователь или группа*  <br> **RoleDefinition**: *Определение роли*  |
| AddRoleAssignment(SPWeb Web, SPPrincipal Principal, SPRoleDefinition RoleDefinition) | Добавляет права пользователю или группе Principal на узел.  <br> **Web**: *Узел*  <br> **Principal**: *Пользователь или группа*  <br> **RoleDefinition**: *Определение роли*  |
| AddRoleAssignment(SPList List, SPPrincipal Principal, SPRoleDefinition RoleDefinition) | Добавляет права пользователю или группе Principal на список.  <br> **List**: *List*  <br> **Principal**: *Пользователь или группа*  <br> **RoleDefinition**: *Определение роли*  |
| AddRoleAssignment(SPListItem Item, SPPrincipal Principal, SPRoleType RoleType) | Добавляет права пользователю или группе Principal на элемент списка Item.  <br> **Item**: *Элемент списка*  <br> **Principal**: *Пользователь или группа*  <br> **RoleType**: *Стандартный тип роли.*  |
| AddRoleAssignment(SPWeb Web, SPPrincipal Principal, SPRoleType RoleType) | Добавляет права пользователю или группе Principal на узел.  <br> **Web**: *Узел*  <br> **Principal**: *Пользователь или группа*  <br> **RoleType**: *Стандартный тип роли.*  |
| AddRoleAssignment(SPList List, SPPrincipal Principal, SPRoleType RoleType) | Добавляет права пользователю или группе Principal на список.  <br> **List**: *Список*  <br> **Principal**: *Пользователь или группа*  <br> **RoleType**: *Стандартный тип роли.*  |
| AddRoleAssignment(SPListItem Item, SPPrincipal Principal, String RoleDefinitionName) | Добавляет права пользователю или группе Principal на элемент списка Item.  <br> **Item**: *Элемент списка*  <br> **Principal**: *Пользователь или группа*  <br> **RoleDefinitionName**: *Название роли. Например: "Совместная работа", "Чтение" и т.д.*  |
| AddRoleAssignment(SPWeb Web, SPPrincipal Principal, String RoleDefinitionName) | Добавляет права пользователю или группе Principal на узел.  <br> **Web**: *Узел*  <br> **Principal**: *Пользователь или группа*  <br> **RoleDefinitionName**: *Название роли. Например: "Совместная работа", "Чтение" и т.д.*  |
| AddRoleAssignment(SPList List, SPPrincipal Principal, String RoleDefinitionName) | Добавляет права пользователю или группе Principal на список.  <br> **List**: *Список*  <br> **Principal**: *Пользователь или группа*  <br> **RoleDefinitionName**: *Название роли. Например: "Совместная работа", "Чтение" и т.д.*  |
| ChangeRoleAssignment(SPListItem Item, SPPrincipal Principal, String DeleteRoleDefinitionName, String AddRoleDefinitionName) | Замена прав пользователя или группы Principal на элемент списка Item.  <br> **Item**: *Элемент списка*  <br> **Principal**: *Пользователь или группа*  <br> **DeleteRoleDefinitionName**: *Название роли для удаления. Например: "Совместная работа", "Чтение" и т.д.*  <br> **AddRoleDefinitionName**: *Название роли для добавления. Например: "Совместная работа", "Чтение" и т.д.*  |
| ChangeRoleAssignment(SPWeb Web, SPPrincipal Principal, String DeleteRoleDefinitionName, String AddRoleDefinitionName) | Замена прав пользователя или группы Principal на узел.  <br> **Web**: *Узел*  <br> **Principal**: *Пользователь или группа*  <br> **DeleteRoleDefinitionName**: *Название роли для удаления. Например: "Совместная работа", "Чтение" и т.д.*  <br> **AddRoleDefinitionName**: *Название роли для добавления. Например: "Совместная работа", "Чтение" и т.д.*  |
| ChangeRoleAssignment(SPList List, SPPrincipal Principal, String DeleteRoleDefinitionName, String AddRoleDefinitionName) | Замена прав пользователя или группы Principal на список.  <br> **List**: *Список*  <br> **Principal**: *Пользователь или группа*  <br> **DeleteRoleDefinitionName**: *Название роли для удаления. Например: "Совместная работа", "Чтение" и т.д.*  <br> **AddRoleDefinitionName**: *Название роли для добавления. Например: "Совместная работа", "Чтение" и т.д.*  |
| ChangeRoleAssignment(SPListItem Item, SPPrincipal Principal, SPRoleDefinition DeleteRoleDefinition, SPRoleDefinition AddRoleDefinition) | Замена прав пользователя или группы Principal на элемент списка Item.  <br> **Item**: *Элемент списка*  <br> **Principal**: *Пользователь или группа*  <br> **DeleteRoleDefinition**: *Определение роли для удаления. Например: "Совместная работа", "Чтение" и т.д.*  <br> **AddRoleDefinition**: *Определение роли для добавления. Например: "Совместная работа", "Чтение" и т.д.*  |
| ChangeRoleAssignment(SPWeb Web, SPPrincipal Principal, SPRoleDefinition DeleteRoleDefinition, SPRoleDefinition AddRoleDefinition) | Замена прав пользователя или группы Principal на узел.  <br> **Web**: *Узел*  <br> **Principal**: *Пользователь или группа*  <br> **DeleteRoleDefinition**: *Определение роли для удаления. Например: "Совместная работа", "Чтение" и т.д.*  <br> **AddRoleDefinition**: *Определение роли для добавления. Например: "Совместная работа", "Чтение" и т.д.*  |
| ChangeRoleAssignment(SPList List, SPPrincipal Principal, SPRoleDefinition DeleteRoleDefinition, SPRoleDefinition AddRoleDefinition) | Замена прав пользователя или группы Principal на список.  <br> **List**: *Список*  <br> **Principal**: *Пользователь или группа*  <br> **DeleteRoleDefinition**: *Определение роли для удаления. Например: "Совместная работа", "Чтение" и т.д.*  <br> **AddRoleDefinition**: *Определение роли для добавления. Например: "Совместная работа", "Чтение" и т.д.*  |
| GetRoleAssignment(SPListItem Item, SPPrincipal Principal) | Получение установленных прав пользователя или группы Principal на элемент списка Item.             Если прав нет, то возвращает пустой SPRoleAssignment.  <br> **Item**: *Элемент списка.*  <br> **Principal**: *Пользователь или группа.*  |
| GetRoleAssignment(SPWeb Web, SPPrincipal Principal) | Получение установленных прав пользователя или группы Principal на узел.             Если прав нет, то возвращает пустой SPRoleAssignment.  <br> **Web**: *Узел.*  <br> **Principal**: *Пользователь или группа.*  |
| GetRoleAssignment(SPList List, SPPrincipal Principal) | Получение установленных прав пользователя или группы Principal на список.             Если прав нет, то возвращает пустой SPRoleAssignment.  <br> **List**: *Список.*  <br> **Principal**: *Пользователь или группа.*  |
| GetPrincipals(SPListItem Item, Boolean ExceptRestrictedRead) | Получение всех Principal'ов у элемента списка Item.  <br> **Item**: *Элемент списка*  <br> **ExceptRestrictedRead**: *Если true, то не учитываются Principal'ы только с уровнем разрешений "Ограниченный доступ" (или "Restricted Read" для англоязычных сайтов).              Значение по умолчанию: true*  |
| GetPrincipals(SPWeb Web, Boolean ExceptRestrictedRead) | Получение всех Principal'ов у узла.  <br> **Web**: *Узел*  <br> **ExceptRestrictedRead**: *Если true, то не учитываются Principal'ы только с уровнем разрешений "Ограниченный доступ" (или "Restricted Read" для англоязычных сайтов).              Значение по умолчанию: true*  |
| GetPrincipals(SPList List, Boolean ExceptRestrictedRead) | Получение всех Principal'ов у списка.  <br> **List**: *Список*  <br> **ExceptRestrictedRead**: *Если true, то не учитываются Principal'ы только с уровнем разрешений "Ограниченный доступ" (или "Restricted Read" для англоязычных сайтов).              Значение по умолчанию: true*  |
| GetPrincipalsExceptList(SPListItem Item, List&lt;String&gt; ExceptRoleDefinitionNameList, Boolean ExceptRestrictedRead) | Получение всех Principal'ов у элемента списка Item.             Не учитываются Principal'ы, у которых есть права только из списка ExceptRoleDefinitionNameList  <br> **Item**: *Элемент списка*  <br> **ExceptRoleDefinitionNameList**: *Список названий уровней разрешений, которые необходимо игнорировать.*  <br> **ExceptRestrictedRead**: *Если true, то не учитываются Principal'ы только с уровнем разрешений "Ограниченный доступ" (или "Restricted Read" для англоязычных сайтов).              Значение по умолчанию: true*  |
| GetPrincipalsExceptList(SPWeb Web, List&lt;String&gt; ExceptRoleDefinitionNameList, Boolean ExceptRestrictedRead) | Получение всех Principal'ов у узла.             Не учитываются Principal'ы, у которых есть права только из списка ExceptRoleDefinitionNameList  <br> **Web**: *Узел.*  <br> **ExceptRoleDefinitionNameList**: *Список названий уровней разрешений, которые необходимо игнорировать.*  <br> **ExceptRestrictedRead**: *Если true, то не учитываются Principal'ы только с уровнем разрешений "Ограниченный доступ" (или "Restricted Read" для англоязычных сайтов).              Значение по умолчанию: true*  |
| GetPrincipalsExceptList(SPList List, List&lt;String&gt; ExceptRoleDefinitionNameList, Boolean ExceptRestrictedRead) | Получение всех Principal'ов у списка.             Не учитываются Principal'ы, у которых есть права только из списка ExceptRoleDefinitionNameList  <br> **List**: *Список.*  <br> **ExceptRoleDefinitionNameList**: *Список названий уровней разрешений, которые необходимо игнорировать.*  <br> **ExceptRestrictedRead**: *Если true, то не учитываются Principal'ы только с уровнем разрешений "Ограниченный доступ" (или "Restricted Read" для англоязычных сайтов).              Значение по умолчанию: true*  |
| GetRoleAssignmentsExceptList(SPListItem Item, List&lt;String&gt; ExceptRoleDefinitionNameList) | Получение всех установленных прав на элемент списка Item.             Не учитываются RoleAssignment'ы, у которых есть RoleDefinition.Name только из списка ExceptRoleDefinitionNameList  <br> **Item**: *Элемент списка*  <br> **ExceptRoleDefinitionNameList**: *Список названий уровней разрешений, которые необходимо игнорировать.*  |
| GetRoleAssignmentsExceptList(SPWeb Web, List&lt;String&gt; ExceptRoleDefinitionNameList) | Получение всех установленных прав на узел.             Не учитываются RoleAssignment'ы, у которых есть RoleDefinition.Name только из списка ExceptRoleDefinitionNameList  <br> **Web**: *Узел*  <br> **ExceptRoleDefinitionNameList**: *Список названий уровней разрешений, которые необходимо игнорировать.*  |
| GetRoleAssignmentsExceptList(SPList List, List&lt;String&gt; ExceptRoleDefinitionNameList) | Получение всех установленных прав на список.             Не учитываются RoleAssignment'ы, у которых есть RoleDefinition.Name только из списка ExceptRoleDefinitionNameList  <br> **List**: *Список*  <br> **ExceptRoleDefinitionNameList**: *Список названий уровней разрешений, которые необходимо игнорировать.*  |
| GetRoleDefinition(SPWeb Web, String RoleName) | Получение SPRoleDefinition по названию роли.  <br> **Web**: *Узел, на котором необходимо совершить действие с правами на объект SharePoint.*  <br> **RoleName**: *Название роли. Возможные значения: Совместная работа, Изменение, Чтение и т.д.*  |
| GetRoleDefinition(SPWeb Web, SPRoleType RoleType) | Получение RoleDefinition по типу стандартной роли.  <br> **Web**: *Узел, на котором необходимо совершить действие с правами на объект SharePoint.*  <br> **RoleType**: *Тип стандартной роли*  |
| DeleteRoleDefinitionBinding(SPRoleAssignment RoleAssignment, SPRoleDefinition RoleDefinition) | Удаление роли RoleDefinition из коллекции ролей RoleDefinitionBindings для установленных прав RoleAssignment на элемент списка.  <br> **RoleAssignment**: *Установленные права на элемент списка*  <br> **RoleDefinition**: *Роль для удаления*  |
| DeletePermissionsByRoleDefinition(SPListItem Item, SPRoleDefinition RoleDefinition) | Удаление всех прав определенной роли RoleDefinition из элемента списка Item  <br> **Item**: *Элемент списка*  <br> **RoleDefinition**: *Роль для удаления*  |
| DeletePermissionsByRoleDefinition(SPWeb Web, SPRoleDefinition RoleDefinition) | Удаление всех прав определенной роли RoleDefinition из узла  <br> **Web**: *Узел.*  <br> **RoleDefinition**: *Роль для удаления*  |
| DeletePermissionsByRoleDefinition(SPList List, SPRoleDefinition RoleDefinition) | Удаление всех прав определенной роли RoleDefinition из списка  <br> **List**: *Список.*  <br> **RoleDefinition**: *Роль для удаления*  |
| DeletePermissionsByRoleTitle(SPListItem Item, String RoleTitle) | Удаление всех прав определенного типа RoleTitle из элемента списка Item  <br> **Item**: *Элемент списка*  <br> **RoleTitle**: *Название роли (в уровнях разрешений site collection) для удаления. Возможные значения: Совместная работа, Изменение, Чтение и т.д.*  |
| DeletePermissionsByRoleTitle(SPWeb Web, String RoleTitle) | Удаление всех прав определенного типа RoleTitle из узла  <br> **Web**: *Узел*  <br> **RoleTitle**: *Название роли (в уровнях разрешений site collection) для удаления. Возможные значения: Совместная работа, Изменение, Чтение и т.д.*  |
| DeletePermissionsByRoleTitle(SPList List, String RoleTitle) | Удаление всех прав определенного типа RoleTitle из списка  <br> **List**: *Список*  <br> **RoleTitle**: *Название роли (в уровнях разрешений site collection) для удаления. Возможные значения: Совместная работа, Изменение, Чтение и т.д.*  |
| DeletePermissionsByRoleType(SPListItem Item, SPRoleType RoleType) | Удаление всех прав определенного типа RoleType из элемента списка Item  <br> **Item**: *Элемент списка*  <br> **RoleType**: *Тип стандартной роли для удаления*  |
| DeletePermissionsByRoleType(SPWeb Web, SPRoleType RoleType) | Удаление всех прав определенного типа RoleType из узла  <br> **Web**: *Узел.*  <br> **RoleType**: *Тип стандартной роли для удаления*  |
| DeletePermissionsByRoleType(SPList List, SPRoleType RoleType) | Удаление всех прав определенного типа RoleType из списка  <br> **List**: *Список.*  <br> **RoleType**: *Тип стандартной роли для удаления*  |
| DeletePermissionByRoleDefinition(SPListItem Item, SPPrincipal Principal, SPRoleDefinition RoleDefinition) | Удаление прав пользователя или группы Principal определенной роли RoleDefinition из элемента списка Item.  <br> **Item**: *Элемент списка*  <br> **Principal**: *Пользователь или группа. Параметр может быть следующих типов: Principal, User, Group*  <br> **RoleDefinition**: *Роль для удаления*  |
| DeletePermissionByRoleDefinition(SPWeb Web, SPPrincipal Principal, SPRoleDefinition RoleDefinition) | Удаление прав пользователя или группы Principal определенной роли RoleDefinition из узла.  <br> **Web**: *Узел*  <br> **Principal**: *Пользователь или группа. Параметр может быть следующих типов: Principal, User, Group*  <br> **RoleDefinition**: *Роль для удаления*  |
| DeletePermissionByRoleDefinition(SPList List, SPPrincipal Principal, SPRoleDefinition RoleDefinition) | Удаление прав пользователя или группы Principal определенной роли RoleDefinition из списка.  <br> **List**: *Список*  <br> **Principal**: *Пользователь или группа. Параметр может быть следующих типов: Principal, User, Group*  <br> **RoleDefinition**: *Роль для удаления*  |
| DeletePermissionByRoleTitle(SPListItem Item, SPPrincipal Principal, String RoleTitle) | Удаление прав пользователя или группы Principal определенного типа RoleTitle из элемента списка Item  <br> **Item**: *Элемент списка*  <br> **Principal**: *Пользователь или группа. Параметр может быть следующих типов: Principal, User, Group*  <br> **RoleTitle**: *Название роли (в уровнях разрешений site collection) для удаления. Возможные значения: Совместная работа, Изменение, Чтение и т.д.*  |
| DeletePermissionByRoleTitle(SPWeb Web, SPPrincipal Principal, String RoleTitle) | Удаление прав пользователя или группы Principal определенного типа RoleTitle из узла  <br> **Web**: *Узел.*  <br> **Principal**: *Пользователь или группа. Параметр может быть следующих типов: Principal, User, Group*  <br> **RoleTitle**: *Название роли (в уровнях разрешений site collection) для удаления. Возможные значения: Совместная работа, Изменение, Чтение и т.д.*  |
| DeletePermissionByRoleTitle(SPList List, SPPrincipal Principal, String RoleTitle) | Удаление прав пользователя или группы Principal определенного типа RoleTitle из списка  <br> **List**: *Список.*  <br> **Principal**: *Пользователь или группа. Параметр может быть следующих типов: Principal, User, Group*  <br> **RoleTitle**: *Название роли (в уровнях разрешений site collection) для удаления. Возможные значения: Совместная работа, Изменение, Чтение и т.д.*  |
| DeletePermissionByRoleType(SPListItem Item, SPPrincipal Principal, SPRoleType RoleType) | Удаление прав пользователя или группы Principal определенного типа RoleType из элемента списка Item  <br> **Item**: *Элемент списка*  <br> **Principal**: *Пользователь или группа. Параметр может быть следующих типов: Principal, User, Group*  <br> **RoleType**: *Тип стандартной роли для удаления*  |
| DeletePermissionByRoleType(SPWeb Web, SPPrincipal Principal, SPRoleType RoleType) | Удаление прав пользователя или группы Principal определенного типа RoleType из узла  <br> **Web**: *Узел.*  <br> **Principal**: *Пользователь или группа. Параметр может быть следующих типов: Principal, User, Group*  <br> **RoleType**: *Тип стандартной роли для удаления*  |
| DeletePermissionByRoleType(SPList List, SPPrincipal Principal, SPRoleType RoleType) | Удаление прав пользователя или группы Principal определенного типа RoleType из списка  <br> **List**: *Список.*  <br> **Principal**: *Пользователь или группа. Параметр может быть следующих типов: Principal, User, Group*  <br> **RoleType**: *Тип стандартной роли для удаления*  |
| DeletePermissions(SPListItem Item, SPPrincipal Principal, Boolean ExceptRestrictedRead) | Удаление всех прав пользователя или группы Principal из элемента списка Item.  <br> **Item**: *Элемент списка*  <br> **Principal**: *Пользователь или группа. Параметр может быть следующих типов: Principal, User, Group*  <br> **ExceptRestrictedRead**: *Если true, то удалятся все уровни разрешений, кроме "Ограниченный доступ" (или "Restricted Read" для англоязычных сайтов).              Значение по умолчанию: true*  |
| DeletePermissions(SPWeb Web, SPPrincipal Principal, Boolean ExceptRestrictedRead) | Удаление всех прав пользователя или группы Principal из узла.  <br> **Web**: *Узел.*  <br> **Principal**: *Пользователь или группа. Параметр может быть следующих типов: Principal, User, Group*  <br> **ExceptRestrictedRead**: *Если true, то удалятся все уровни разрешений, кроме "Ограниченный доступ" (или "Restricted Read" для англоязычных сайтов).              Значение по умолчанию: true*  |
| DeletePermissions(SPList List, SPPrincipal Principal, Boolean ExceptRestrictedRead) | Удаление всех прав пользователя или группы Principal из списка.  <br> **List**: *Список.*  <br> **Principal**: *Пользователь или группа. Параметр может быть следующих типов: Principal, User, Group*  <br> **ExceptRestrictedRead**: *Если true, то удалятся все уровни разрешений, кроме "Ограниченный доступ" (или "Restricted Read" для англоязычных сайтов).              Значение по умолчанию: true*  |
| DeletePermissionsExceptList(SPListItem Item, SPPrincipal Principal, List&lt;String&gt; ExceptRoleDefinitionNameList, Boolean ExceptRestrictedRead) | Удаление всех прав пользователя или группы Principal из элемента списка Item, кроме ExceptRoleDefinitionList.  <br> **Item**: *Элемент списка*  <br> **Principal**: *Пользователь или группа. Параметр может быть следующих типов: Principal, User, Group*  <br> **ExceptRoleDefinitionNameList**: *Список названий уровней разрешений, которые необходимо оставить.*  <br> **ExceptRestrictedRead**: *Если true, то удалятся все уровни разрешений, кроме "Ограниченный доступ" (или "Restricted Read" для англоязычных сайтов).              Значение по умолчанию: true*  |
| DeletePermissionsExceptList(SPWeb Web, SPPrincipal Principal, List&lt;String&gt; ExceptRoleDefinitionNameList, Boolean ExceptRestrictedRead) | Удаление всех прав пользователя или группы Principal из узла, кроме ExceptRoleDefinitionList.  <br> **Web**: *Узел*  <br> **Principal**: *Пользователь или группа. Параметр может быть следующих типов: Principal, User, Group*  <br> **ExceptRoleDefinitionNameList**: *Список названий уровней разрешений, которые необходимо оставить.*  <br> **ExceptRestrictedRead**: *Если true, то удалятся все уровни разрешений, кроме "Ограниченный доступ" (или "Restricted Read" для англоязычных сайтов).              Значение по умолчанию: true*  |
| DeletePermissionsExceptList(SPList List, SPPrincipal Principal, List&lt;String&gt; ExceptRoleDefinitionNameList, Boolean ExceptRestrictedRead) | Удаление всех прав пользователя или группы Principal из списка, кроме ExceptRoleDefinitionList.  <br> **List**: *Список*  <br> **Principal**: *Пользователь или группа. Параметр может быть следующих типов: Principal, User, Group*  <br> **ExceptRoleDefinitionNameList**: *Список названий уровней разрешений, которые необходимо оставить.*  <br> **ExceptRestrictedRead**: *Если true, то удалятся все уровни разрешений, кроме "Ограниченный доступ" (или "Restricted Read" для англоязычных сайтов).              Значение по умолчанию: true*  |
| IsEquivalent(SPPrincipal Principal, SPPrincipal ComparePrincipal) | Сравнение Principal'ов по Title'ам без учета регистра  <br> **Principal**: *Пользователь или группа*  <br> **ComparePrincipal**: *Пользователь или группа*  |

#### Samples
```csharp

/// <summary>
/// Добавляет права пользователю или группе. 
/// </summary>
/// <param name="item">Элемент списка</param>
/// <param name="principal">SPGroup or SPUser</param>
private void AddPermissions(SPListItem item, SPPrincipal principal)
{
    // добавление прав "Совместная работа" группе "Ulteam Site - посетители" на элемент спика item.
    item.AddRoleAssignment(principal, "Совместная работа");

    // то же самое, только используя RoleDefinition
    SPRoleDefinition roleDefinition = item.Web.GetRoleDefinition("Совместная работа");
    item.AddRoleAssignment(principal, roleDefinition);
}
```
```csharp

/// <summary>
/// Замена прав пользователя или группы. 
/// </summary>
/// <param name="item">Элемент списка</param>
/// <param name="principal">SPGroup or SPUser</param>
private void ChangePermissions(SPListItem item, SPPrincipal principal)
{
    // замена прав у группы с "Совместная работа" на "Чтение"
    item.ChangeRoleAssignment(principal, "Совместная работа", "Чтение");

    // то же самое, используя RoleDefinition'ы
    SPRoleDefinition deleteRoleDefinition = item.Web.GetRoleDefinition("Совместная работа");
    SPRoleDefinition addRoleDefinition = item.Web.GetRoleDefinition("Чтение");

    item.ChangeRoleAssignment(principal, deleteRoleDefinition, addRoleDefinition);
}
```
```csharp

/// <summary>
/// Удаление прав определенного типа у всех пользователей или групп. 
/// </summary>
/// <param name="item">Элемент списка</param>
private void DeleteAllPermissions(SPListItem item)
{
    // удаление прав "Совместная работа" у всех пользователей и групп.
    item.DeletePermissionsByRoleTitle("Совместная работа");

    // то же самое, используя RoleDefinition
    SPRoleDefinition roleDefinition = item.Web.GetRoleDefinition("Совместная работа");
    item.DeletePermissionsByRoleDefinition(roleDefinition);

    // то же самое, используя RoleType
    item.DeletePermissionsByRoleType(SPRoleType.Contributor);
}
```
```csharp

/// <summary>
/// Удаление всех прав у пользователя или группы. 
/// </summary>
/// <param name="item">Элемент списка</param>
/// <param name="principal">SPGroup or SPUser</param>
private void DeleteAllPermissionsByPrincipal(SPListItem item, SPPrincipal principal)
{
    // удаление всех уровней разрешений для группы, кроме "Ограниченный доступ"
    item.DeletePermissions(principal);

    List<string> roleDefinitionNameList = new List<string>
    {
        "Чтение",
        "Только просмотр"
    };

    // удаление всех уровней разрешений для группы, кроме "Чтение", "Только просмотр" и "Ограниченный доступ"
    item.DeletePermissionsExceptList(principal, roleDefinitionNameList);
}
```
```csharp

/// <summary>
/// Удаление определенных прав пользователя или группы. 
/// </summary>
/// <param name="item">Элемент списка</param>
/// <param name="principal">SPGroup or SPUser</param>
private void DeletePermissionByPrincipal(SPListItem item, SPPrincipal principal)
{
    // удаление прав "Совместная работа" у всех пользователей и групп.
    item.DeletePermissionByRoleTitle(principal, "Совместная работа");

    // то же самое, используя RoleDefinition
    SPRoleDefinition roleDefinition = item.Web.GetRoleDefinition("Совместная работа");
    item.DeletePermissionByRoleDefinition(principal, roleDefinition);

    // то же самое, используя RoleType
    item.DeletePermissionByRoleType(principal, SPRoleType.Contributor);
}
```
```csharp

/// <summary>
/// Получение всех пользователей и групп, имеющих права на элемент списка.
/// </summary>
/// <param name="item">Элемент списка</param>
private List<SPPrincipal> GetPrincipalsExceptList(SPListItem item)
{
    List<string> roleDefinitionNameList = new List<string>
    {
        "Чтение",
        "Только просмотр"
    };

    // получение всех пользователей и групп, 
    // у которых есть какие-нибудь уровни разрешений на элемент Item, 
    // кроме "Чтение", "Только просмотр" и "Ограниченный доступ"
    return item.GetPrincipalsExceptList(roleDefinitionNameList);
}
```
```csharp

/// <summary>
/// В этом примере все права (кроме прав "Полный доступ") у всех пользователей и групп заменяются на права "Чтение".
/// Плюс добавляются отдельно права "Совместная работа" для создателя элемента списка.
/// </summary>
/// <param name="item">Элемент списка</param>
private void SetPermissions(SPListItem item)
{
    SPFieldUserValue authorValue = item.GetValueAsUser("Author");
    SPPrincipal authorPrincipal = item.Web.SiteUsers.GetByID(authorValue.LookupId);

    SPRoleDefinition editorRoleDefinition = item.Web.GetRoleDefinition("Совместная работа");
    SPRoleDefinition readerRoleDefinition = item.Web.GetRoleDefinition("Чтение");

    // получаем список всех пользователей и групп с правами, кроме ограниченного доступа
    List<SPPrincipal> principalList = item.GetPrincipals();

    // добавляем всем права на чтение
    foreach (SPPrincipal principal in principalList)
        item.AddRoleAssignment(principal, readerRoleDefinition);
    
    // удаляем права у всех остальных пользователей или групп, кроме прав "Чтение" и "Полный доступ"
    List<string> exceptRoleDefinitionList = new List<string>
    {
        "Чтение",
        "Полный доступ"
    };
    foreach (SPPrincipal principal in principalList)
        item.DeletePermissionsExceptList(principal, exceptRoleDefinitionList, true);

    // добавляем инициатору отдельные права "Совместная работа"
    item.AddRoleAssignment(authorPrincipal, editorRoleDefinition);
}
```
