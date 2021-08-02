---
title: Ulteam.SharePoint 
permalink: /nuget/Ulteam.SharePoint/lists/
sidebar:
  nav: "nuget"
---

### Lists Class
Namespace: Ulteam.SharePoint

#### Description
Класс для работы со списками.


#### Methods

| Name | Description |
|-|-|
| AddFieldToList(SPList List, FieldSchema FieldScheme) | Добавление нового поля в список.  <br> **List**: *Список SharePoint.*  <br> **FieldScheme**: *Настройки поля.*  |
| AddListItem(SPList List, String Data, Object} ) | Создание элемента списка по Data.  <br> **List**: *Список для добавления.*  <br> **Data**: *Поля со значениями.*  |
| CreateList(SPWeb Web, String ListTitle, List&lt;FieldSchema&gt; FieldSchemaList, Boolean EnableVersioning, SPListTemplateType Type) | Создание списка и добавление новых полей из ListScheme.  <br> **Web**: *Узел, на который добавляется список.*  <br> **ListTitle**: *Название списка.*  <br> **FieldSchemaList**: *Настройки полей для добавления. Значение по умолчанию: null.*  <br> **EnableVersioning**: *Добавить версионность в список.*  <br> **Type**: *Template type.*  |
| CreateOrUpdateList(SPWeb Web, ListInfo ListInfo, SPListTemplateType Type) | Создание списка.  <br> **Web**: *Узел, на который добавляется список.*  <br> **ListInfo**: *List metadata.*  <br> **Type**: *Template type.*  |
| CreateOrUpdateListView(SPList List, ViewInfo Info) | Create or update existing list view.  <br> **List**: *SharePoint list.*  <br> **Info**: *List metadata.*  |
| GetItemsByTextField(SPList list, String key, String value, UInt32 rowLimit) | Получение элементов списка по значению в текстовом поле  <br> **list**: *Список*  <br> **key**: *Internal name поля*  <br> **value**: *Значение поля*  <br> **rowLimit**: *Максимальное количество элементов*  |
| GetListByUrl(SPWeb Web, String ListUrl) | Получение списка по URL. Если список не существует, то возвращается null.  <br> **Web**: *Узел списка. Если в корневом узле site collection, то null.*  <br> **ListUrl**: *Url списка (после web.ServerRelativeUrl). Например, "/Lists/MyTestList".*  |
| SetFormJSLink(SPList List, PAGETYPE PageType, String JsLinkUrl) | Set JSLink property for SharePoint list form.  <br> **List**: *SharePoint list.*  <br> **PageType**: *SharePoint SPForm.Type prop.*  <br> **JsLinkUrl**: *JSLink value.*  |
| UpdateItem(SPListItem Item, String Data, Object} ) | Обновление элемента списка с флагом AllowUnsafeUpdates = true.  <br> **Item**: *Элемент списка.*  <br> **Data**: *Поля со значениями для обновления.*  |
| UpdateList(SPList List) | Обновление списка с флагом AllowUnsafeUpdates = true.  <br> **List**: *Список.*  |

#### Samples
```csharp

/// <summary>
/// Добавление полей разных типов в список SharePoint.
/// </summary>
public void AddFieldToList()
{
    SPList list = Settings.Mock.Lists["ListsTestList"];
    SPList lookupList = Settings.Mock.Lists["LookupList"];

    List<FieldSchema> fieldValueListScheme = new List<FieldSchema>
    {
        new FieldSchema("TextField", "", "TextField", FieldSchemaType.Text),
        new FieldSchema("NoteField", "", "NoteField", FieldSchemaType.Note),
        new FieldSchema("NumberField", "", "NumberField", FieldSchemaType.Number),
        new FieldSchema("UserField", "", "UserField", FieldSchemaType.User),
        new FieldSchema("MultiUserField", "", "MultiUserField", FieldSchemaType.UserMulti),
        new FieldSchema("ChoiceField", "", "ChoiceField", FieldSchemaType.Choice, new List<string> { "Choice test 1", "Choice test 2" }),
        new FieldSchema("EmptyChoiceField", "", "EmptyChoiceField", FieldSchemaType.Choice, new List<string> {}),
        new FieldSchema("MultiChoiceField", "", "MultiChoiceField", FieldSchemaType.MultiChoice, new List<string> { "Choice test 1", "Choice test 2" }),
        new FieldSchema("BooleanField", "", "BooleanField", FieldSchemaType.Boolean),
        new FieldSchema("DateTimeField", "", "DateTimeField", FieldSchemaType.DateTime),
        new FieldSchema("LookupField", "", "LookupField", FieldSchemaType.Lookup, lookupList.ID, "Title"),
        new FieldSchema("LookupFieldByUrl", "", "LookupFieldByUrl", FieldSchemaType.Lookup, "/Lists/LookupList", "Title"),
        new FieldSchema("MultiLookupField", "", "MultiLookupField", FieldSchemaType.LookupMulti, lookupList.ID, "Title")
    };

    foreach (FieldSchema fieldScheme in fieldValueListScheme)
        list.AddFieldToList(fieldScheme);
}
```
```csharp

/// <summary>
/// Добавление элемента в список SharePoint.
/// </summary>
public void AddItem()
{
    SPList list = Settings.Mock.Lists["ListsTestList"];
    SPUser user1 = Settings.Mock.Users[0];
    SPUser user2 = Settings.Mock.Users[1];
    SPUser user3 = Settings.Mock.Users[2];

    List<SPUser> userList = new List<SPUser>
    {
        user1,
        user2
    };

    Dictionary<string, object> itemData = new Dictionary<string, object>
    {
        { "Title", "Field Value Test 2" },
        { "TextField", "Test text" },
        { "NumberField", 10 },
        { "UserField", user1 },
        { "MultiUserField", FieldValue.SetValueAsMultiUser(userList) },
        { "ChoiceField", "Choice 1" },
        { "MultiChoiceField", FieldValue.SetValueAsMultiChoice("Choice 1;Choice 2", ';') },
        { "BooleanField", true },
        { "DateTimeField", new DateTime(2018, 1, 1, 5, 0, 0) },
        { "LookupField", FieldValue.SetValueAsLookup("1") },
        { "MultiLookupField", FieldValue.SetValueAsMultiLookup("1;2", ';') }
    };
    SPListItem newItem = list.AddListItem(itemData);
}
```
```csharp

/// <summary>
/// Добавление списка SharePoint.
/// </summary>
public void CreateList()
{
    SPWeb web = Settings.Mock.Web;

    // список для добавление полей Lookup и LookupMulti
    SPList lookupList = Settings.Mock.Lists["LookupList"];

    List<string> choices = new List<string> { "Choice 1", "Choice 2" };
    List<FieldSchema> fieldSchema = new List<FieldSchema>
    {
        new FieldSchema("TextField", "Description", FieldSchemaType.Text),
        new FieldSchema("NumberField", "Description", FieldSchemaType.Number),
        new FieldSchema("UserField", "Description", FieldSchemaType.User),
        new FieldSchema("MultiUserField", "Description", FieldSchemaType.UserMulti),
        new FieldSchema("ChoiceField", "Description", "Choice Field", FieldSchemaType.Choice, choices),
        new FieldSchema("MultiChoiceField", "Description", "Multi Choice Field", FieldSchemaType.MultiChoice, choices),
        new FieldSchema("BooleanField", "Description", FieldSchemaType.Boolean),
        new FieldSchema("DateTimeField", "Description", FieldSchemaType.DateTime),
        new FieldSchema("LookupField", "Description", "Lookup Field", FieldSchemaType.Lookup, lookupList.ID, "Title"),
        new FieldSchema("MultiLookupField", "Description", "Multi Lookup Field", FieldSchemaType.LookupMulti, lookupList.ID, "Title")
    };

    // создание списка с дополнительными полями
    SPList newList = web.CreateList("NewList", fieldSchema);

    // создание списка без дополнительных полей
    SPList newStandardList = web.CreateList("NewStandardList");
}
```
```csharp

/// <summary>
/// Получение списка SharePoint.
/// </summary>
public void GetList()
{
    SPWeb web = Settings.Mock.Web;

    SPList listByUrl = web.GetListByUrl("/Lists/GetListTest");
}
```
