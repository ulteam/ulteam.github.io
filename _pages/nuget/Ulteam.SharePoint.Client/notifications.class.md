---
title: Ulteam.SharePoint.Client 
permalink: /nuget/Ulteam.SharePoint.Client/notifications/
sidebar:
  nav: "nuget"
---

### Notifications Class
Namespace: Ulteam.SharePoint.Client

#### Description
Класс по работе с уведомлениями.
            Для стабильной работы методов класса лучше использовать списки, созданные с помощью ListInitialization класса.

#### Constructors

| Name | Description |
|-|-|
| Notifications(ClientContext Context, List&lt;DataItem&gt; DataItems, List NotificationList, List NotificationSettingsList, List NotificationUserList, List ReminderNotificationList, List ReminderSettingsList) | Инициирование объекта для отправки уведомлений.  <br> **Context**: *SharePoint site collection context.*  <br> **DataItems**: *Список объектов с данными, необходимыми для формирования уведомления.*  <br> **NotificationList**: *Список уведомлений.*  <br> **NotificationSettingsList**: *Список настроек уведомлений.*  <br> **NotificationUserList**: *Список для добавления пользователей в уведомления.*  <br> **ReminderNotificationList**: *Список Reminder'ов.*  <br> **ReminderSettingsList**: *Список настроек Reminder'ов.*  |
| Notifications(ClientContext Context, List&lt;DataItem&gt; DataItems, String NotificationListUrl, String NotificationSettingsListUrl, String NotificationUserListUrl, String ReminderNotificationListUrl, String ReminderSettingsListUrl) | Инициирование объекта для отправки уведомлений.  <br> **Context**: *SharePoint site collection context.*  <br> **DataItems**: *Список объектов с данными, необходимыми для формирования уведомления.*  <br> **NotificationListUrl**: *Url списка уведомлений. По умолчанию: 'Lists/NotificationList'.*  <br> **NotificationSettingsListUrl**: *Url списка настроек уведомлений. По умолчанию: 'Lists/NotificationSettings'.*  <br> **NotificationUserListUrl**: *Url списка для добавления пользователей в уведомления. По умолчанию: 'Lists/NotificationUserList'.*  <br> **ReminderNotificationListUrl**: *Url списка Reminder'ов.*  <br> **ReminderSettingsListUrl**: *Url списка настроек Reminder'ов.*  |

#### Methods

| Name | Description |
|-|-|
| CreateByProcessStep(ListItem ProcessStep, DateTime ReminderStartDate, String ItemType, String ItemId, String StepNumber, Boolean AddIfCreated) | Создание уведомления по настройке шага процесса (элемент списка ProcessStepList).  <br> **ProcessStep**: *Шаг процесса (элемент списка ProcessStepList).*  <br> **ReminderStartDate**: *Дата первого Reminder'а. В случае обычного уведомления значение ни на что не влияет.*  <br> **ItemType**: *Тип элемента списка.*  <br> **ItemId**: *Id элемента списка.*  <br> **StepNumber**: *Id шага процесса уведомления.*  <br> **AddIfCreated**: *Укажите, надо ли добавлять уведомление, если уже добавлено уведомление с такими же ItemType, ItemId, StepNumber и NotificationSetting.              Значение по умолчанию: false.*  |
| CreateBySetting(NotificationSetting Setting, DateTime ReminderStartDate, String ItemType, String ItemId, String StepNumber, Boolean AddIfCreated) | Создание уведомления по настройке уведомления (элементу из NotificationSettings).  <br> **Setting**: *Настройка уведомления (элемент из NotificationSettings).*  <br> **ReminderStartDate**: *Дата первого Reminder'а. В случае обычного уведомления значение ни на что не влияет.*  <br> **ItemType**: *Тип элемента списка.*  <br> **ItemId**: *Id элемента списка.*  <br> **StepNumber**: *Id шага процесса уведомления.*  <br> **AddIfCreated**: *Укажите, надо ли добавлять уведомление, если уже добавлено уведомление с такими же ItemType, ItemId, StepNumber и NotificationSetting.              Значение по умолчанию: false.*  |
| CreateByTitle(String NotificationTitle, DateTime ReminderStartDate, String ItemType, String ItemId, String StepNumber, Boolean AddIfCreated) | Создание уведомления по названию в списке NotificationSettings.  <br> **NotificationTitle**: *Название уведомления (поле Title в NotificationSettings).*  <br> **ReminderStartDate**: *Дата первого Reminder'а. В случае обычного уведомления значение ни на что не влияет.*  <br> **ItemType**: *Тип элемента списка.*  <br> **ItemId**: *Id элемента списка.*  <br> **StepNumber**: *Id шага процесса уведомления.*  <br> **AddIfCreated**: *Укажите, надо ли добавлять уведомление, если уже добавлено уведомление с такими же ItemType, ItemId, StepNumber и NotificationSetting.              Значение по умолчанию: false.*  |
| DefaultParseTemplate(String Template) | Парсинг шаблона по тегам Filled, Field, FormUrl, History.  <br> **Template**: *Шаблон для парсинга.*  |
| EndReminders(String ItemType) | Завершение Reminder'ов, отфильтрованных по ItemType.  <br> **ItemType**: *Тип элемента списка.*  |
| EndReminders(String ItemType, String ItemId) | Завершение Reminder'ов, отфильтрованных по ItemType, ItemId.  <br> **ItemType**: *Тип элемента списка.*  <br> **ItemId**: *Id элемента списка.*  |
| EndReminders(String ItemType, String ItemId, String StepNumber) | Завершение Reminder'ов, отфильтрованных по ItemType, ItemId, StepNumber.  <br> **ItemType**: *Тип элемента списка.*  <br> **ItemId**: *Id элемента списка.*  <br> **StepNumber**: *Id шага процесса уведомления.*  |
| GetNotificationUsers(FieldLookupValue[] LookupValues) | Получение пользователей для уведомления через lookupValues из NotificationUserList.  <br> **LookupValues**: *Lookup'ы к списку NotificationUserList.*  |
| SendNotifications() | Отправка уведомлений на почту по элементам списка NotificationList с Sent = false.  |
| UpdateReminders(DateTime CheckDate) | Обновление всех Reminder'ов по условию (End = 0 AND NotificationDate <= CheckDate).             Если Reminder (элемент списка ReminderNotificationList) подходит под эти условия,             то создается элемент в NotificationList и к Reminder.NotificationDate добавляется ReminderSendPeriod из списка NotificationSettings.  <br> **CheckDate**: *Дата, с которой необходимо сравнить NotificationDate.*  |

#### Samples
```csharp

/// <summary>
/// Создание уведомлений для шага процесса.
/// Для стабильной работы методов класса лучше использовать списки, созданные с помощью ListInitialization класса.
/// </summary>
public void CreateNotificationByProcessStep()
{
    ClientContext context = TestSettings.Context;
    
    // список настроек шагов процесса
    List processList = context.GetListByTitle("ProcessStepList");

    // шаг процесса
    ListItem processStep = processList.GetItemById(1);

    context.Load(processStep);
    context.ExecuteQuery();

    // Данные, по которым формируется уведомление.
    List<DataItem> dataItems = GetDataItems();

    Notifications notifications = new Notifications(context, dataItems);

    // Формирование уведомлений и добавление обычных уведомлений в NotificationList 
    // и reminder'ов в ReminderNotificationList
    bool created = notifications.CreateByProcessStep(
        processStep,

        // Дата первой отправки Reminder'а. Если простое уведомление, то дата ни на что не влияет
        DateTime.Now,

        // ItemType в NotificationList 
        "ProcessStepTest",

        // ItemId в NotificationList
        "100",

        // StepNumber в NotificationList
        "1000",

        // Если false, то новый элемент в NotificationList добавляется только в случае, 
        // если не существует элемента с такими же ItemType, ItemId, StepNumber
        false 
    );

    // добавление Reminder'ов, для которых NotificationDate из ReminderNotificationList меньше DateTime.Now
    notifications.UpdateReminders(DateTime.Now);

    // отправка уведомлений из NotificationList на почту (без процесса).
    notifications.SendNotifications();
}
```
```csharp

/// <summary>
/// Создание уведомления по элементу из списка NotificationSettings.
/// Для стабильной работы методов класса лучше использовать списки, созданные с помощью ListInitialization класса.
/// </summary>
public void CreateNotificationBySetting()
{
    ClientContext context = TestSettings.Context;

    // Данные, по которым формируется уведомление.
    List<DataItem> dataItems = GetDataItems();

    Notifications notifications = new Notifications(context, dataItems);

    // получение настройки уведомления
    NotificationSetting setting = new NotificationSetting(context, notifications.NotificationSettingsList);
    setting.GetByTitle("NotificationTest");

    // Формирование уведомления и добавление  в NotificationList 
    // или в ReminderNotificationList
    bool created = notifications.CreateBySetting(
        setting,

        // Дата первой отправки Reminder'а. Если простое уведомление, то дата ни на что не влияет
        DateTime.Now,

        // ItemType в NotificationList 
        "ProcessStepTest",

        // ItemId в NotificationList
        "100",

        // StepNumber в NotificationList
        "1000",

        // Если false, то новый элемент в NotificationList добавляется только в случае, 
        // если не существует элемента с такими же ItemType, ItemId, StepNumber
        false
    );

    // добавление Reminder'ов, для которых NotificationDate из ReminderNotificationList меньше DateTime.Now
    notifications.UpdateReminders(DateTime.Now);

    // отправка уведомлений из NotificationList на почту (без процесса).
    notifications.SendNotifications();
}
```
```csharp

/// <summary>
/// Создание уведомления по названию элемента из списка NotificationSettings.
/// Для стабильной работы методов класса лучше использовать списки, созданные с помощью ListInitialization класса.
/// </summary>
public void CreateNotificationBySettingTitle()
{
    ClientContext context = TestSettings.Context;

    // Данные, по которым формируется уведомление.
    List<DataItem> dataItems = GetDataItems();

    Notifications notifications = new Notifications(context, dataItems);

    // Формирование уведомления и добавление  в NotificationList 
    // или в ReminderNotificationList
    bool created = notifications.CreateByTitle(
        "NotificationTest",

        // Дата первой отправки Reminder'а. Если простое уведомление, то дата ни на что не влияет
        DateTime.Now,

        // ItemType в NotificationList 
        "ProcessStepTest",

        // ItemId в NotificationList
        "100",

        // StepNumber в NotificationList
        "1000",

        // Если false, то новый элемент в NotificationList добавляется только в случае, 
        // если не существует элемента с такими же ItemType, ItemId, StepNumber
        false
    );

    // добавление Reminder'ов, для которых NotificationDate из ReminderNotificationList меньше DateTime.Now
    notifications.UpdateReminders(DateTime.Now);

    // отправка уведомлений из NotificationList на почту (без процесса).
    notifications.SendNotifications();
}
```
```csharp

/// <summary>
/// Формирование данных, по которым формируются уведомления.
/// </summary>
private List<DataItem> GetDataItems()
{
    // шаг в HTML истории процесса
    XmlNode stepNode = GetStepNode();

    // основной список, например, с заявками
    ListItem mainItem = TestSettings.NotificationTestList.GetItemById(1);

    // дополнительный список, например, с задачи процесса
    ListItem secondItem = TestSettings.NotificationTestList.GetItemById(2);

    TestSettings.Context.Load(mainItem);
    TestSettings.Context.Load(secondItem);
    TestSettings.Context.ExecuteQuery();

    return new List<DataItem>
    {
        // из mainItem будут подставляться значения в теги с type="Main"
        // например, <Field type='Main' name='Title' />
        new DataItem("Main", mainItem),

        // из secondItem будут подставляться значения в теги с type="Task"
        // например, <Field type='Task' name='Title' />
        new DataItem("Task", secondItem),

        // из stepNode будут подставляться значения в теги вида:
        // <History type='MainProcess' name='history-approver' />
        // Где 'history-approver' - класс в stepNode.
        // Подставится значение stepNode.innerText
        new DataItem("MainProcess", stepNode)
    };
}
```
```csharp

/// <summary>
/// Шаг процесса
/// </summary>
private XmlNode GetStepNode()
{
    string userIdList = $"{MockData.UserId1},{MockData.UserId3},{MockData.UserId3}";
    string history = string.Format(@"
        <div class='node' useridlist='{0}'>
            <div>
                <span class='history-approver'>History User Name</span>
            </div>
        </div>", userIdList);
    XmlDocument document = XmlHelper.GetXmlDocument(history);

    return document.SelectSingleNode("//div[@class='node']");
}
```
