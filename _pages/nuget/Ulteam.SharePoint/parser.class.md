---
title: Ulteam.SharePoint 
permalink: /nuget/Ulteam.SharePoint/parser/
sidebar:
  nav: "nuget"
---

### Parser Class
Namespace: Ulteam.SharePoint

#### Description
Класс для парсинга текста.

#### Constructors

| Name | Description |
|-|-|
| Parser(String Template) | Добавление шаблона.              В шаблоне может быть несколько корневых элементов.  <br> **Template**: *Шаблон для парсинга.*  |

#### Methods

| Name | Description |
|-|-|
| GetFieldValue(SPListItem Item, SPField Field, ParseSetting Setting) | Получение текстового значения из Field в зависимости от типа поля.  <br> **Item**: *Элемент списка.*  <br> **Field**: *Поле для получения значения.*  <br> **Setting**: *Настройка парсинга.*  |
| GetResult(Boolean AsText) | Получение результата в виде текста.  <br> **AsText**: *Вернуть результат как InnerText. Если false, то вернется XML. Значение по умолчанию: false.*  |
| ParseFieldTag(SPListItem Item, String ItemType) | Парсинг тега Field.              Вместо тега подставляется значение поля (name) элемента списка (type) SharePoint.              Возможные атрибуты тега:             type (тип элемента списка),             name (internal name поля в списке),             format (формат поля типа дата и время),             separator (разделитель для полей MultiUser, MultiChoice, MultiLookup),             truevalue (значение, если в поле стоит true),             falsevalue (значение, если в поле стоит false).  <br> **Item**: *Элемент списка, из которого будут браться значения.*  <br> **ItemType**: *Тип элемента списка, указанное в атрибуте type тега. Если параметр не указан, обрабатываются теги без атрибута type, либо с type=''.*  |
| ParseFilledTag(SPListItem Item, String ItemType) | Парсинг тега Filled.             Если значение в поле (name) элемента списка (type) не пустое, то вернется InnerXml тега.             Возможные атрибуты тега:              type (тип элемента списка),             name (internal name поля в списке).  <br> **Item**: *Элемент списка, из которого будут браться значения.*  <br> **ItemType**: *Тип элемента списка, указанный в атрибуте type тега. Если параметр не указан, обрабатываются теги без атрибута type, либо с type=''.*  |
| ParseFormUrlTag(SPListItem Item, String ItemType) | Парсинг тега FormUrl.             Заменяется на <a href='{name}'>{InnerXml}</a>             Возможные атрибуты тега:              type (тип элемента списка),             name (internal name поля в списке).  <br> **Item**: *Элемент списка, для которого находятся FormUrl.*  <br> **ItemType**: *Тип элемента списка, указанный в атрибуте type тега. Если параметр не указан, обрабатываются теги без атрибута type, либо с type=''.*  |
| ParseHistoryTag(XmlNode Node, String NodeType) | Парсинг тега History.             Возможные атрибуты тега:              type (тип элемента списка),             name - название класса html элемента, из которого необходимо взять значение (InnerText).  <br> **Node**: *Узел из HTML истории процесса с шагом, из которого необходимо взять данные.*  <br> **NodeType**: *Тип элемента, указанное в атрибуте type тега. Если параметр не указан, обрабатываются теги без атрибута type, либо с type=''.*  |

#### Samples
```csharp

/// <summary>
/// Пример парсинга HTML.
/// Парсятся теги Field, Filled, FormUrl
/// </summary>
public void ExampleParseFunction()
{
    SPList list = Settings.Mock.Lists["ParserList"];

    SPListItemCollection items = list.GetItems();

    SPListItem mainItem = items[0];
    SPListItem taskItem = items[1];

    string template = @"
    <div>
     <div>
      TextField:<Field name='Title' />
     </div>
     <div>
      TextField:<Field type='Task' name='TextField' />
     </div>
     <div>
      NumberField:<Field type='Task' name='NumberField' />
     </div>
     <div>
      UserField:<Field type='Task' name='UserField' />
     </div>
     <div>
      MultiUserField1:<Field type='Task' name='MultiUserField' />
     </div>
     <div>
      MultiUserField2:<Field type='Task' name='MultiUserField' separator='#; ' />
     </div>
     <div>
      ChoiceField:<Field type='Task' name='ChoiceField' />
     </div>
     <div>
      MultiChoiceField1:<Field type='Task' name='MultiChoiceField' />
     </div>
     <div>
      MultiChoiceField2:<Field type='Task' name='MultiChoiceField' separator='#; ' />
     </div>
     <div>
      BooleanField1:<Field type='Task' name='BooleanField' />
     </div>
     <div>
      BooleanField2:<Field type='Task' name='BooleanField' truevalue='да' falsevalue='нет' />
     </div>
     <div>
      DateTimeField1:<Field type='Task' name='DateTimeField' />
     </div>
     <div>
      DateTimeField2:<Field type='Task' name='DateTimeField' format='yyyy-MM-ddTmm:ss' />
     </div>
     <div>
      LookupField:<Field type='Task' name='LookupField' />
     </div>
     <div>
      MultiLookupField1:<Field type='Task' name='MultiLookupField' />
     </div>
     <div>
      MultiLookupField2:<Field type='Task' name='MultiLookupField' separator='#; ' />
     </div>
     <div>
            EmptyField:<Filled type='Main' name='TextField'><div>InnerXml</div></Filled>
        </div>
        <div>
      <FormUrl name='NewForm'>
       <div>NewForm</div>
      </FormUrl>
     </div>
     <div>
      <FormUrl name='DisplayForm'>
       <div>DisplayForm</div>
      </FormUrl>
     </div>
     <div>
      <FormUrl name='EditForm' type='Task'>
       <div>TaskEditForm</div>
      </FormUrl>
     </div>
    </div>";

    Parser parser = new Parser(template);

    parser.ParseFieldTag(mainItem);
    parser.ParseFieldTag(taskItem, "Task");

    parser.ParseFilledTag(taskItem, "Main");

    parser.ParseFormUrlTag(mainItem);
    parser.ParseFormUrlTag(taskItem, "Task");

    string result = parser.GetResult();

    // вернется значение:
    //<div>
    //	<div>TextField:Field Value Test 1</div>
    //	<div>TextField:Test text</div>
    //	<div>NumberField:10</div>
    //	<div>UserField:Test User 01</div>
    //	<div>MultiUserField1:Test User 01, Test User 02</div>
    //	<div>MultiUserField2:Test User 01#; Test User 02</div>
    //	<div>ChoiceField:Choice 1</div>
    //	<div>MultiChoiceField1:Choice 1, Choice 2</div>
    //	<div>MultiChoiceField2:Choice 1#; Choice 2</div>
    //	<div>BooleanField1:true</div>
    //	<div>BooleanField2:да</div>
    //	<div>DateTimeField1:01.01.2018</div>
    //	<div>DateTimeField2:2018-01-01T00:00</div>
    //	<div>LookupField:Title 1</div>
    //	<div>MultiLookupField1:Title 1, Title 2</div>
    //	<div>MultiLookupField2:Title 1#; Title 2</div>
    //	<div>EmptyField:<div>InnerXml</div></div>
    //	<div>
    //		<a href="https://{tenantName}.sharepoint.com/{webUrl}/Lists/ParserList/NewForm.aspx">
    //			<div>NewForm</div>
    //		</a>
    //	</div>
    //	<div>
    //		<a href="https://{tenantName}.sharepoint.com/{webUrl/Lists/ParserList/DispForm.aspx?ID=1">
    //			<div>DisplayForm</div>
    //		</a>
    //	</div>
    //	<div>
    //		<a href="https://{tenantName}.sharepoint.com/{webUrl}/Lists/ParserList/EditForm.aspx?ID=2">
    //			<div>TaskEditForm</div>
    //		</a>
    //	</div>
    //</div>
}
    }
```
