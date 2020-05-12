---
title: Ulteam.SharePoint.Client 
permalink: /nuget/Ulteam.SharePoint.Client/fieldvalue/
sidebar:
  nav: "nuget"
---

### FieldValue Class
Namespace: Ulteam.SharePoint.Client

#### Description
Класс по работе со значениями полей в элементе списка SharePoint.


#### Methods

| Name | Description |
|-|-|
| GetValue&lt;T&gt;(ListItem Item, String Key) | Возвращает значение поля типа T элемента списка.  <br> **Item**: *Элемент списка*  <br> **Key**: *Internal Name поля*  |
| GetValueAsBool(ListItem Item, String Key) | Возвращает логическое значение поля элемента списка.  <br> **Item**: *Элемент списка*  <br> **Key**: *Internal Name поля*  |
| GetValueAsChoice(ListItem Item, String Key) | Возвращает значение поля типа "Выбор" (без множественных значений) элемента списка.  <br> **Item**: *Элемент списка*  <br> **Key**: *Internal Name поля*  |
| GetValueAsDateTime(ListItem Item, String Key) | Возвращает значение поля типа "Дата и время" (UTC) элемента списка.             Если не удалось перевести в DateTime, то возвращается DateTime.MinValue.  <br> **Item**: *Элемент списка*  <br> **Key**: *Internal Name поля*  |
| GetValueAsInt(ListItem Item, String Key) | Возвращает числовое значение поля элемента списка.  <br> **Item**: *Элемент списка*  <br> **Key**: *Internal Name поля*  |
| GetValueAsLookup(ListItem Item, String Key) | Возвращает значение поля типа "Подстановка без множественного выбора" элемента списка.             Если в поле доступен множественный выбор, то вернется только первое значение.  <br> **Item**: *Элемент списка*  <br> **Key**: *Internal Name поля*  |
| GetValueAsMultiChoice(ListItem Item, String Key) | Возвращает значение поля типа "Выбор" с множественными значениями элемента списка.  <br> **Item**: *Элемент списка*  <br> **Key**: *Internal Name поля*  |
| GetValueAsMultiLookup(ListItem Item, String Key) | Возвращает значение поля типа "Подстановка с множественным выбором" элемента списка.             Если в поле недоступен множественный выбор, то вернется массив с одним значением.  <br> **Item**: *Элемент списка*  <br> **Key**: *Internal Name поля*  |
| GetValueAsMultiUser(ListItem Item, String Key) | Возвращает значение поля типа "Пользователь или группа с множественным выбором" элемента списка.             Если в поле недоступен множественный выбор, то вернется массив с одним значением.  <br> **Item**: *Элемент списка*  <br> **Key**: *Internal Name поля*  |
| GetValueAsText(ListItem Item, String Key) | Возвращает текстовое значение поля элемента списка.  <br> **Item**: *Элемент списка*  <br> **Key**: *Internal Name поля*  |
| GetValueAsUser(ListItem Item, String Key) | Возвращает значение поля типа "Пользователь или группа без множественного выбора" элемента списка.             Если в поле доступен множественный выбор, то вернется только первое значение.  <br> **Item**: *Элемент списка*  <br> **Key**: *Internal Name поля*  |
| SetValueAsLookup(String LookupId) | Возвращает значение для записи в поле типа "Подстановка без множественного выбора" элемента списка.  <br> **LookupId**: *Id элемента списка в подстановке*  |
| SetValueAsMultiLookup(String LookupIdList, Char Separator) | Возвращает значение для записи в поле типа "Подстановка с множественным выбором" элемента списка.  <br> **LookupIdList**: *Список Id элементов списка в подстановке*  <br> **Separator**: *Разделитель в списке*  |
| SetValueAsMultiUser(String UserIdList, Char Separator) | Возвращает значение для записи в поле типа "Пользователь или группа с множественным выбором" элемента списка.  <br> **UserIdList**: *Список Id пользователей*  <br> **Separator**: *Разделитель в списке*  |
| SetValueAsUser(String UserId) | Возвращает значение для записи в поле типа "Пользователь или группа без множественного выбора" элемента списка.  <br> **UserId**: *Id пользователя*  |
| GetEmails(FieldUserValue Value, ClientContext Context) | Получение Email'ов пользователей в группе SharePoint или Email одного пользователя,              если FieldUserValue - это пользователь.  <br> **Value**: *Значение поля типа "Пользователь или группа".*  <br> **Context**: *SharePoint site collection context.*  |
| GetEmails(List&lt;FieldUserValue&gt; Values, ClientContext Context) | Получение Email'ов пользователей в группе SharePoint или Email одного пользователя,              если FieldUserValue - это пользователь.  <br> **Values**: *Список значений поля типа "Пользователь или группа".*  <br> **Context**: *SharePoint site collection context.*  |
| GetEmailsFromGroup(Group Group) | Получение Email'ов пользователей в группе SharePoint.  <br> **Group**: *Группа SharePoint.*  |
| GetUserFieldType(FieldUserValue Value, ClientContext Context) | Определяем тип FieldUserValue: пользователь или группа.  <br> **Value**: *Значение поля типа "Пользователь или группа".*  <br> **Context**: *SharePoint site collection context.*  |

#### Samples
```csharp

/// <summary>
/// Получение списка  FieldUserValue.
/// </summary>
public void GetEmails()
{
    ClientContext context = TestSettings.Context;
    FieldUserValue group = new FieldUserValue { LookupId = MockData.GroupId1 };
    FieldUserValue user = new FieldUserValue { LookupId = MockData.UserId1 };

    List<string> emails = group.GetEmails(context); // вернет список email'в всех пользователей в группе

    List<FieldUserValue> fieldUserValues = new List<FieldUserValue> { group, user };
    emails = fieldUserValues.GetEmails(context); // вернет список email'в из всех FieldUserValue и удалит совпадения
}
```
```csharp

/// <summary>
/// Получение значений из ListItem'а
/// </summary>
public void GetFieldValues()
{
    ListItem item = TestSettings.FieldValueListItems[1];

    string textValue = item.GetValueAsText("TextField");
    bool boolValue = item.GetValueAsBool("BooleanField");
    DateTime dateTimeValue = item.GetValueAsDateTime("DateTimeField");
    int intValue = item.GetValueAsInt("NumberField");

    string choiceValue = item.GetValueAsChoice("ChoiceField");
    string[] multiChoiceValue = item.GetValueAsMultiChoice("MultiChoiceField");

    FieldLookupValue fieldLookupValue = item.GetValueAsLookup("LookupField");
    FieldLookupValue[] fieldLookupValues = item.GetValueAsMultiLookup("MultiLookupField");

    FieldUserValue fieldUserValue = item.GetValueAsUser("UserField");
    FieldUserValue[] fieldUserValues = item.GetValueAsMultiUser("MultiUserField");
}
```
```csharp

/// <summary>
/// Определение, пользователь или группа в FieldUserValue.
/// </summary>
public void GetUserFieldType()
{
    ClientContext context = TestSettings.Context;
    FieldUserValue group = new FieldUserValue { LookupId = MockData.GroupId1 };
    FieldUserValue user = new FieldUserValue { LookupId = MockData.UserId1 };

    group.GetUserFieldType(context); // return FieldValueType.Group
    user.GetUserFieldType(context); // return FieldValueType.User
}
```
```csharp

/// <summary>
/// Запись значений в ListItem.
/// </summary>
public void SetFieldValues()
{
    ClientContext context = TestSettings.Context;
    List list = TestSettings.FieldValueList;

    ListItemCreationInformation itemCreateInfo = new ListItemCreationInformation();
    ListItem newItem = list.AddItem(itemCreateInfo);

    string userId = MockData.UserId1.ToString(); // id пользователя в site collection
    string userIdList = $"{MockData.UserId1.ToString()},{MockData.UserId2.ToString()}";
    
    newItem["UserField"] = FieldValue.SetValueAsUser(userId); // userId = "11"
    newItem["MultiUserField"] = FieldValue.SetValueAsMultiUser(userIdList, ','); // userIdList = "11,12"
    newItem["LookupField"] = FieldValue.SetValueAsLookup("1");
    newItem["MultiLookupField"] = FieldValue.SetValueAsMultiLookup("1,2", ',');

    newItem.Update();
    context.ExecuteQuery();
}
```
