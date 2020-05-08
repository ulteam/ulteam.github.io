---
title: Ulteam.SharePoint 
permalink: /nuget/Ulteam.SharePoint/fieldvalue/
sidebar:
  nav: "nuget"
---

### FieldValue Class
Namespace: Ulteam.SharePoint

#### Description
Класс по работе со значениями полей в элементе списка SharePoint.


#### Methods

| Name | Description |
|-|-|
| GetValue&lt;T&gt;(SPListItem Item, String Key) | Возвращает значение поля типа T элемента списка.  <br> **Item**: *Элемент списка*  <br> **Key**: *Internal Name поля*  |
| GetValueAsBool(SPListItem Item, String Key) | Возвращает логическое значение поля элемента списка.  <br> **Item**: *Элемент списка*  <br> **Key**: *Internal Name поля*  |
| GetValueAsChoice(SPListItem Item, String Key) | Возвращает значение поля типа "Выбор" (без множественных значений) элемента списка.  <br> **Item**: *Элемент списка*  <br> **Key**: *Internal Name поля*  |
| GetValueAsDateTime(SPListItem Item, String Key, Boolean AsUTC) | Возвращает значение поля типа "Дата и время" элемента списка.             Если не удалось перевести в DateTime, то возвращается DateTime.MinValue.  <br> **Item**: *Элемент списка*  <br> **Key**: *Internal Name поля*  <br> **AsUTC**: *Перевести в UTC формат.*  |
| GetValueAsInt(SPListItem Item, String Key) | Возвращает числовое значение поля элемента списка.  <br> **Item**: *Элемент списка*  <br> **Key**: *Internal Name поля*  |
| GetValueAsLookup(SPListItem Item, String Key) | Возвращает значение поля типа "Подстановка без множественного выбора" элемента списка.             Если в поле доступен множественный выбор, то вернется только первое значение.  <br> **Item**: *Элемент списка*  <br> **Key**: *Internal Name поля*  |
| GetValueAsMultiChoice(SPListItem Item, String Key) | Возвращает значение поля типа "Выбор" с множественными значениями элемента списка.  <br> **Item**: *Элемент списка*  <br> **Key**: *Internal Name поля*  |
| GetValueAsMultiLookup(SPListItem Item, String Key) | Возвращает значение поля типа "Подстановка с множественным выбором" элемента списка.             Если в поле недоступен множественный выбор, то вернется массив с одним значением.  <br> **Item**: *Элемент списка*  <br> **Key**: *Internal Name поля*  |
| GetValueAsMultiUser(SPListItem Item, String Key) | Возвращает значение поля типа "Пользователь или группа с множественным выбором" элемента списка.             Если в поле недоступен множественный выбор, то вернется массив с одним значением.  <br> **Item**: *Элемент списка*  <br> **Key**: *Internal Name поля*  |
| GetValueAsText(SPListItem Item, String Key) | Возвращает текстовое значение поля элемента списка.  <br> **Item**: *Элемент списка*  <br> **Key**: *Internal Name поля*  |
| GetValueAsUrl(SPListItem Item, String Key) | Возвращает значение поля типа "Изображение или ссылка" элемента списка.  <br> **Item**: *Элемент списка*  <br> **Key**: *Internal Name поля*  |
| GetValueAsUser(SPListItem Item, String Key) | Возвращает значение поля типа "Пользователь или группа без множественного выбора" элемента списка.             Если в поле доступен множественный выбор, то вернется только первое значение.  <br> **Item**: *Элемент списка*  <br> **Key**: *Internal Name поля*  |
| SetValueAsLookup(String LookupId) | Возвращает значение для записи в поле типа "Подстановка без множественного выбора" элемента списка.  <br> **LookupId**: *Id элемента списка в подстановке*  |
| SetValueAsMultiChoice(String valueList, Char Separator) | Возвращает значение для записи в поле типа "Выбор с множественными значениями" элемента списка.  <br> **valueList**: *Список значений.*  <br> **Separator**: *Разделитель в списке.*  |
| SetValueAsMultiLookup(String LookupIdList, Char Separator) | Возвращает значение для записи в поле типа "Подстановка с множественным выбором" элемента списка.  <br> **LookupIdList**: *Список Id элементов списка в подстановке.*  <br> **Separator**: *Разделитель в списке.*  |
| SetValueAsMultiUser(List&lt;SPUser&gt; Users) | Возвращает значение для записи в поле типа "Пользователь или группа с множественным выбором" элемента списка.  <br> **Users**: *Список пользователей.*  |
| SetValueAsMultiUser(List&lt;SPFieldUserValue&gt; UserValues) | Возвращает значение для записи в поле типа "Пользователь или группа с множественным выбором" элемента списка.  <br> **UserValues**: *Список пользователей.*  |
| SetValueAsMultiUser(String UserIdList, Char Separator) | Возвращает значение для записи в поле типа "Пользователь или группа с множественным выбором" элемента списка.  <br> **UserIdList**: *Список Id пользователей*  <br> **Separator**: *Разделитель в списке*  |
| SetValueAsUrl(String Url, String Description) | Returns value for saving to SPListItem Url field.  <br> **Url**: *Link Url value.*  <br> **Description**: *Link Description value.*  |
| SetValueAsUser(SPWeb Web, String UserId) | Возвращает значение для записи в поле типа "Пользователь или группа без множественного выбора" элемента списка.  <br> **Web**: *Узел, на котором добавлен пользователь с UserId.*  <br> **UserId**: *Id пользователя.*  |
| GetEmails(SPFieldUserValue Value, SPSite Site) | Получение Email'ов пользователей в группе SharePoint или Email одного пользователя,              если FieldUserValue - это пользователь.  <br> **Value**: *Значение поля типа "Пользователь или группа".*  <br> **Site**: *Site collection.*  |
| GetEmails(List&lt;SPFieldUserValue&gt; Values, SPSite Site) | Получение Email'ов пользователей в группе SharePoint или Email одного пользователя,              если FieldUserValue - это пользователь.  <br> **Values**: *Список значений поля типа "Пользователь или группа".*  <br> **Site**: *Site collection.*  |
| GetEmailsFromGroup(SPGroup Group) | Получение Email'ов пользователей в группе SharePoint.  <br> **Group**: *Группа SharePoint.*  |
| GetUserFieldType(SPFieldUserValue Value, SPSite Site) | Определяем тип SPFieldUserValue: пользователь или группа.  <br> **Value**: *Значение поля типа "Пользователь или группа".*  <br> **Site**: *Site collection.*  |

#### Samples
```csharp

/// <summary>
/// Get email list by SPFieldUserValue.
/// </summary>
public void GetEmails()
{
    SPSite site = Settings.Mock.Site;

    SPGroup group = Settings.Mock.Groups[0];
    SPUser user = Settings.Mock.Users[0];

    SPFieldUserValue groupValue = new SPFieldUserValue { LookupId = group.ID };
    SPFieldUserValue userValue = new SPFieldUserValue { LookupId = user.ID };

    // returns email list for all users in group
    List<string> emails = groupValue.GetEmails(site);

    List<SPFieldUserValue> fieldUserValues = new List<SPFieldUserValue> { groupValue, userValue };
    // returns email list for all users in group and email for userValue and delete duplicate values
    emails = fieldUserValues.GetEmails(site);
}
```
```csharp

/// <summary>
/// Get field values from SPListItem
/// </summary>
public void GetFieldValues()
{
    SPListItem item = Settings.Mock.Lists["FieldValueList"].GetItemById(1);
    
    string textValue = item.GetValueAsText("TextField");
    bool boolValue = item.GetValueAsBool("BooleanField");
    DateTime dateTimeValue = item.GetValueAsDateTime("DateTimeField");
    int intValue = item.GetValueAsInt("NumberField");

    string choiceValue = item.GetValueAsChoice("ChoiceField");
    SPFieldMultiChoiceValue multiChoiceValue = item.GetValueAsMultiChoice("MultiChoiceField");

    SPFieldLookupValue fieldLookupValue = item.GetValueAsLookup("LookupField");
    SPFieldLookupValueCollection fieldLookupValues = item.GetValueAsMultiLookup("MultiLookupField");

    SPFieldUserValue fieldUserValue = item.GetValueAsUser("UserField");
    SPFieldUserValueCollection fieldUserValues = item.GetValueAsMultiUser("MultiUserField");
}
```
```csharp

/// <summary>
/// Get SPFieldUserValue type: user or group.
/// </summary>
public void GetUserFieldType()
{
    SPSite site = Settings.Mock.Site;

    SPGroup group = Settings.Mock.Groups[0];
    SPUser user = Settings.Mock.Users[0];

    SPFieldUserValue groupValue = new SPFieldUserValue { LookupId = group.ID };
    SPFieldUserValue userValue = new SPFieldUserValue { LookupId = user.ID };

    groupValue.GetUserFieldType(site); // returns FieldValueType.Group
    userValue.GetUserFieldType(site); // returns FieldValueType.User
}
```
```csharp

/// <summary>
/// Set values to SPListItem.
/// </summary>
public void SetFieldValues()
{
    SPWeb web = Settings.Mock.Web;

    SPUser user1 = Settings.Mock.Users[0];
    SPUser user2 = Settings.Mock.Users[1];

    string userId = user1.ID.ToString(); // user id from site collection user list
    string userIdList = $"{user1.ID.ToString()},{user2.ID.ToString()}";

    SPList list = Settings.Mock.Lists["FieldValueList"];

    SPListItem newItem = list.AddItem();

    newItem["UserField"] = FieldValue.SetValueAsUser(web, userId); // userId = "11"
    newItem["MultiUserField"] = FieldValue.SetValueAsMultiUser(userIdList, ','); // userIdList = "11,12"
    newItem["LookupField"] = FieldValue.SetValueAsLookup("1");
    newItem["MultiLookupField"] = FieldValue.SetValueAsMultiLookup("1,2", ',');

    newItem.UpdateItem();

    // ---------------
    // or another way with method AddListItem from Lists class

    Dictionary<string, object> itemData = new Dictionary<string, object>
    {
        { "UserField", FieldValue.SetValueAsUser(web, userId) },
        { "MultiUserField", FieldValue.SetValueAsMultiUser(userIdList, ',') },
        { "LookupField", FieldValue.SetValueAsLookup("1") },
        { "MultiLookupField", FieldValue.SetValueAsMultiLookup("1,2", ',') }
    };

    list.AddListItem(itemData);
}
```
