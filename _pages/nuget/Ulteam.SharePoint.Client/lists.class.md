---
title: Ulteam.SharePoint.Client 
permalink: /nuget/Ulteam.SharePoint.Client/lists/
sidebar:
  nav: "nuget"
---

### Lists Class
Namespace: Ulteam.SharePoint.Client

#### Description
Класс для работы со списками.


#### Methods

| Name | Description |
|-|-|
| AddFieldToList(ClientContext Context, List List, FieldScheme FieldScheme, Boolean ExecuteQuery) | Добавление нового поля в список.  <br> **Context**: *SharePoint site collection context.*  <br> **List**: *Список SharePoint.*  <br> **FieldScheme**: *Настройки поля.*  <br> **ExecuteQuery**: *Если true, то выполняется Context.ExecuteQuery(). Значение по умолчанию: true.*  |
| AddListItem(ClientContext Context, List List, String Data, Object} ExecuteQuery, Boolean ) | Создание элемента списка по Data.  <br> **Context**: *SharePoint site collection context.*  <br> **List**: *Список для добавления.*  <br> **Data**: *Поля со значениями.*  <br> **ExecuteQuery**: *Если true, то выполняется Context.ExecuteQuery(). Значение по умолчанию: true.*  |
| CreateList(ClientContext Context, String ListTitle, List&lt;FieldScheme&gt; FieldSchemeList, Boolean EnableVersioning) | Создание списка и добавление новых полей из ListScheme.  <br> **Context**: *SharePoint site collection context.*  <br> **ListTitle**: *Название списка.*  <br> **FieldSchemeList**: *Настройки полей для добавления. Значение по умолчанию: null.*  <br> **EnableVersioning**: *Добавить версионность в список.*  |
| GetFields(ClientContext Context, List List, Boolean ExecuteQuery) | Получение коллекции полей списка.  <br> **Context**: *SharePoint site collection context.*  <br> **List**: *Список с полями.*  <br> **ExecuteQuery**: *Если true, то выполняется Context.ExecuteQuery(). Значение по умолчанию: true.*  |
| GetListItems(ClientContext Context, List List, String ConditionData, Object} ) | Получение коллекции элементов списка по условию.  <br> **Context**: *SharePoint site collection context.*  <br> **List**: *Список SharePoint.*  <br> **ConditionData**: *Условия для выборки элементов списка. Между выражениями ставится условный оператор AND.             Возможные типы полей: Boolean, Number, Choice, MultiChoice, Lookup, User.*  |
| GetListItems(ClientContext Context, List List, String CamlQuery, String[] Fields, Boolean Recursive, Int32 RowLimit, Boolean Paged) | Получение коллекции элементов списка по CamlQuery.  <br> **Context**: *SharePoint site collection context.*  <br> **List**: *Список SharePoint.*  <br> **CamlQuery**: *Условие для получения элементов списка.              Начинается с тега Where, будет вставляться внуть тега Query.             Если необходима сортировка, то ее надо добавить рядом с тегом Where*  <br> **Fields**: *Необходимые поля.              Если полей в списке много, то CSOM часть из них может потерять.             Поэтому для надежности лучше указывать все необходимые поля.*  <br> **Recursive**: *Получить все элементы из всех папок.*  <br> **RowLimit**: *Максимальное количество элементов списка.*  <br> **Paged**: *Постраничный вывод.*  |
| GetListById(ClientContext Context, Guid ListId, Web Web, Boolean ExecuteQuery) | Получение списка по Guid. Если список не существует, то возвращается null.  <br> **Context**: *SharePoint site collection context.*  <br> **ListId**: *Guid списка.*  <br> **Web**: *Узел списка. Если в корневом узле site collection, то null.*  <br> **ExecuteQuery**: *Если true, то выполняется Context.ExecuteQuery(). Значение по умолчанию: true.*  |
| GetListByTitle(ClientContext Context, String ListTitle, Web Web, Boolean ExecuteQuery) | Получение списка по названию. Если список не существует, то возвращается null.  <br> **Context**: *SharePoint site collection context.*  <br> **ListTitle**: *Название списка.*  <br> **Web**: *Узел списка. Если в корневом узле site collection, то null.*  <br> **ExecuteQuery**: *Если true, то выполняется Context.ExecuteQuery(). Значение по умолчанию: true.*  |
| GetListByUrl(ClientContext Context, String ListUrl, Web Web, Boolean ExecuteQuery) | Получение списка по URL. Если список не существует, то возвращается null.  <br> **Context**: *SharePoint site collection context.*  <br> **ListUrl**: *Url списка (после web.ServerRelativeUrl).*  <br> **Web**: *Узел списка. Если в корневом узле site collection, то null.*  <br> **ExecuteQuery**: *Если true, то выполняется Context.ExecuteQuery(). Значение по умолчанию: true.*  |
| UpdateListItems(ClientContext Context, List List, String CamlQuery, String Data, Object} ) | Обновление коллекции элементов списка по условию.  <br> **Context**: *SharePoint site collection context.*  <br> **List**: *Список для добавления.*  <br> **CamlQuery**: *Условие для получения элементов списка.              Начинается с тега Where, будет вставляться внуть тега Query.             Если необходима сортировка, то ее надо добавить рядом с тегом Where*  <br> **Data**: *Поля со значениями.*  |
| UpdateListItems(ClientContext Context, List List, String ConditionData, Object} Data, String , Object} ) | Обновление коллекции элементов списка по условию.  <br> **Context**: *SharePoint site collection context.*  <br> **List**: *Список для добавления.*  <br> **ConditionData**: *Условия для выборки элементов списка. Между выражениями ставится условный оператор AND.             Возможные типы полей: Boolean, Number, Choice, MultiChoice, Lookup, User.*  <br> **Data**: *Поля со значениями.*  |
| UpdateListItems(ClientContext Context, List List, ListItemCollection Items, String Data, Object} ) | Обновление коллекции элементов списка по условию.  <br> **Context**: *SharePoint site collection context.*  <br> **List**: *Список для добавления.*  <br> **Items**: *Коллекция элементов списка для обновления.*  <br> **Data**: *Поля со значениями.*  |

#### Samples
```csharp

/// <summary>
/// Добавление полей разных типов в список SharePoint.
/// </summary>
public void AddFieldToList()
{
    ClientContext context = TestSettings.Context;
    List list = TestSettings.ListsTestList;

    List<FieldScheme> fieldValueListScheme = new List<FieldScheme>
    {
        new FieldScheme("TextField", "", "TextField", FieldSchemeType.Text),
        new FieldScheme("NoteField", "", "NoteField", FieldSchemeType.Note),
        new FieldScheme("NumberField", "", "NumberField", FieldSchemeType.Number),
        new FieldScheme("UserField", "", "UserField", FieldSchemeType.User),
        new FieldScheme("MultiUserField", "", "MultiUserField", FieldSchemeType.UserMulti),
        new FieldScheme("ChoiceField", "", "ChoiceField", FieldSchemeType.Choice, new List<string> { "Choice test 1", "Choice test 2" }),
        new FieldScheme("EmptyChoiceField", "", "EmptyChoiceField", FieldSchemeType.Choice, new List<string> {}),
        new FieldScheme("MultiChoiceField", "", "MultiChoiceField", FieldSchemeType.MultiChoice, new List<string> { "Choice test 1", "Choice test 2" }),
        new FieldScheme("BooleanField", "", "BooleanField", FieldSchemeType.Boolean),
        new FieldScheme("DateTimeField", "", "DateTimeField", FieldSchemeType.DateTime),
        new FieldScheme("LookupField", "", "LookupField", FieldSchemeType.Lookup, TestSettings.LookupList.Id, "Title"),
        new FieldScheme("LookupFieldByUrl", "", "LookupFieldByUrl", FieldSchemeType.Lookup, "/Lists/LookupList", "Title"),
        new FieldScheme("MultiLookupField", "", "MultiLookupField", FieldSchemeType.LookupMulti, TestSettings.LookupList.Id, "Title")
    };

    foreach (FieldScheme fieldScheme in fieldValueListScheme)
        Lists.AddFieldToList(context, list, fieldScheme, false);

    context.ExecuteQuery();
}
```
```csharp

/// <summary>
/// Добавление элемента в список SharePoint.
/// </summary>
public void AddItem()
{
    ClientContext context = TestSettings.Context;
    List list = TestSettings.ListsTestList;

    Dictionary<string, object> itemData = new Dictionary<string, object>
    {
        { "Title", "Field Value Test 2" },
        { "TextField", "Test text" },
        { "NumberField", 10 },
        { "UserField", new FieldUserValue { LookupId = 9 }},
        { "MultiUserField", new FieldUserValue[]
            {
                new FieldUserValue { LookupId = 11 },
                new FieldUserValue { LookupId = 12 }
            }
        },
        { "ChoiceField", "Choice 1" },
        { "MultiChoiceField", new string[] { "Choice 1", "Choice 2" } },
        { "BooleanField", true },
        { "DateTimeField", new DateTime(2018, 1, 1, 5, 0, 0) },
        { "LookupField", new FieldLookupValue { LookupId = 1 } },
        { "MultiLookupField", new FieldLookupValue[]
            {
                new FieldLookupValue { LookupId = 1 },
                new FieldLookupValue { LookupId = 2 }
            }
        }
    };
    ListItem item = context.AddListItem(list, itemData);
}
```
```csharp

/// <summary>
/// Добавление списка SharePoint.
/// </summary>
public void CreateList()
{
    ClientContext context = TestSettings.Context;

    // список для добавление полей Lookup и LookupMulti
    List lookupList = TestSettings.LookupList;

    List<string> choices = new List<string> { "Choice 1", "Choice 2" };
    List<FieldScheme> fieldValueListScheme = new List<FieldScheme>
    {
        new FieldScheme("TextField", "Description", FieldSchemeType.Text),
        new FieldScheme("NumberField", "Description", FieldSchemeType.Number),
        new FieldScheme("UserField", "Description", FieldSchemeType.User),
        new FieldScheme("MultiUserField", "Description", FieldSchemeType.UserMulti),
        new FieldScheme("ChoiceField", "Description", "Choice Field", FieldSchemeType.Choice, choices),
        new FieldScheme("MultiChoiceField", "Description", "Multi Choice Field", FieldSchemeType.MultiChoice, choices),
        new FieldScheme("BooleanField", "Description", FieldSchemeType.Boolean),
        new FieldScheme("DateTimeField", "Description", FieldSchemeType.DateTime),
        new FieldScheme("LookupField", "Description", "Lookup Field", FieldSchemeType.Lookup, lookupList.Id, "Title"),
        new FieldScheme("MultiLookupField", "Description", "Multi Lookup Field", FieldSchemeType.LookupMulti, lookupList.Id, "Title")
    };

    // создание списка с дополнительными полями
    List newList = context.CreateList("NewList", fieldValueListScheme);

    // создание списка без дополнительных полей
    List newStandardList = context.CreateList("NewStandardList");
}
```
```csharp

/// <summary>
/// Получение списка SharePoint.
/// </summary>
public void GetList()
{
    ClientContext context = TestSettings.Context;

    // создаем тестовый список
    List list = context.CreateList("Lists/GetListTest");

    // методы получения списка
    List listById = context.GetListById(list.Id);
    List listByTitle = context.GetListByTitle("GetListTest");
    List listByUrl = context.GetListByUrl("Lists/GetListTest");
}
```
```csharp

/// <summary>
/// Получение элементов списка SharePoint.
/// </summary>
public void GetListItems()
{
    ClientContext context = TestSettings.Context;
    List list = TestSettings.GetListItemsList;

    // так можно задавать условия для полей разных типов.
    // в GetListItems по этим данным будет сформирован CamlQuery
    Dictionary<string, object> conditionData = new Dictionary<string, object>
    {
        { "Title", "Field Value Test 1" },
        { "TextField", "Test text" },
        { "NumberField", 10 },
        { "UserField", new FieldUserValue { LookupId = MockData.UserId1 } },
        { "ChoiceField", "Choice 1" },
        { "MultiChoiceField", "Choice 1" },
        { "BooleanField", true },
        { "DateTimeField", new DateTime(2018, 1, 1, 5, 0, 0) },
        { "LookupField", new FieldLookupValue { LookupId = 1 } }
    };

    // получение элементов списка, используя Dictionary
    ListItemCollection items = context.GetListItems(list, conditionData);

    // получение элементов списка, используя CamlQuery
    ListItemCollection items2 = context.GetListItems(
        list,
        @"<Where>
            <Eq>
                <FieldRef Name='TextField'/>
                <Value Type='Text'>Test text</Value>
            </Eq>
        </Where>");

    // получение элементов списка, используя CamlQuery и указывая необходимые поля
    // Если полей в списке много, то CSOM часть из них может потерять.
    // Поэтому для надежности лучше указывать все необходимые поля.
    ListItemCollection items3 = context.GetListItems(
        list,
        @"<Where>
            <Eq>
                <FieldRef Name='TextField'/>
                <Value Type='Text'>Test text</Value>
            </Eq>
        </Where>",
        new string[] { "TextField" });

}
```
```csharp

/// <summary>
/// Обновление нескольких элементов списка
/// </summary>
public void UpdateListItems()
{
    ClientContext context = TestSettings.Context;
    List list = TestSettings.GetListItemsList;

    // условие для поиска элементов списка
    Dictionary<string, object> condition = new Dictionary<string, object>()
    {
        { "TextField", "Before update" }
    };

    // поля и значения для обновления
    Dictionary<string, object> newData = new Dictionary<string, object>()
    {
        { "TextField", "After update" }
    };

    // обновление всех элементов списка, удовлетворяющих condition, 
    // значениями из newData
    List<ListItem> items = context.UpdateListItems(list, condition, newData);
}
```
