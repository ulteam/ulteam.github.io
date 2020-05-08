---
title: Ulteam.SharePoint 
permalink: /nuget/Ulteam.SharePoint/notifications/
sidebar:
  nav: "nuget"
---

### Notifications Class
Namespace: Ulteam.SharePoint

#### Description
Класс по работе с уведомлениями.
            Для стабильной работы методов класса лучше использовать списки, созданные с помощью ListInitialization класса.

#### Constructors

| Name | Description |
|-|-|
| Notifications(List&lt;DataItem&gt; DataItems, SPList NotificationList, SPList NotificationSettingsList, SPList NotificationUserList, SPList ReminderNotificationList, SPList ReminderSettingsList) | Инициирование объекта для отправки уведомлений.  <br> **DataItems**: *Список объектов с данными, необходимыми для формирования уведомления.*  <br> **NotificationList**: *Список уведомлений.*  <br> **NotificationSettingsList**: *Список настроек уведомлений.*  <br> **NotificationUserList**: *Список для добавления пользователей в уведомления.*  <br> **ReminderNotificationList**: *Список Reminder'ов.*  <br> **ReminderSettingsList**: *Список настроек Reminder'ов.*  |
| Notifications(SPWeb Web, List&lt;DataItem&gt; DataItems, String NotificationListUrl, String NotificationSettingsListUrl, String NotificationUserListUrl, String ReminderNotificationListUrl, String ReminderSettingsListUrl) | Инициирование объекта для отправки уведомлений.  <br> **Web**: *Узел со списками для работы с уведомлениями.*  <br> **DataItems**: *Список объектов с данными, необходимыми для формирования уведомления.*  <br> **NotificationListUrl**: *Url списка уведомлений. По умолчанию: 'Lists/NotificationList'.*  <br> **NotificationSettingsListUrl**: *Url списка настроек уведомлений. По умолчанию: 'Lists/NotificationSettings'.*  <br> **NotificationUserListUrl**: *Url списка для добавления пользователей в уведомления. По умолчанию: 'Lists/NotificationUserList'.*  <br> **ReminderNotificationListUrl**: *Url списка Reminder'ов.*  <br> **ReminderSettingsListUrl**: *Url списка настроек Reminder'ов.*  |

#### Methods

| Name | Description |
|-|-|
| CreateByProcessStep(SPListItem ProcessStep, DateTime ReminderStartDate, String ItemType, String ItemId, String StepNumber, Boolean AddIfCreated) | Создание уведомления по настройке шага процесса (элемент списка ProcessStepList).  <br> **ProcessStep**: *Шаг процесса (элемент списка ProcessStepList).*  <br> **ReminderStartDate**: *Дата первого Reminder'а. В случае обычного уведомления значение ни на что не влияет.*  <br> **ItemType**: *Тип элемента списка.*  <br> **ItemId**: *Id элемента списка.*  <br> **StepNumber**: *Id шага процесса уведомления.*  <br> **AddIfCreated**: *Укажите, надо ли добавлять уведомление, если уже добавлено уведомление с такими же ItemType, ItemId, StepNumber и NotificationSetting. Значение по умолчанию: false.*  |
| CreateBySetting(NotificationSetting Setting, DateTime ReminderStartDate, String ItemType, String ItemId, String StepNumber, Boolean AddIfCreated) | Создание уведомления по настройке уведомления (элементу из NotificationSettings).  <br> **Setting**: *Настройка уведомления (элемент из NotificationSettings).*  <br> **ReminderStartDate**: *Дата первого Reminder'а. В случае обычного уведомления значение ни на что не влияет.*  <br> **ItemType**: *Тип элемента списка.*  <br> **ItemId**: *Id элемента списка.*  <br> **StepNumber**: *Id шага процесса уведомления.*  <br> **AddIfCreated**: *Укажите, надо ли добавлять уведомление, если уже добавлено уведомление с такими же ItemType, ItemId, StepNumber и NotificationSetting. Значение по умолчанию: false.*  |
| CreateByTitle(String NotificationTitle, DateTime ReminderStartDate, String ItemType, String ItemId, String StepNumber, Boolean AddIfCreated) | Создание уведомления по названию в списке NotificationSettings.  <br> **NotificationTitle**: *Название уведомления (поле Title в NotificationSettings).*  <br> **ReminderStartDate**: *Дата первого Reminder'а. В случае обычного уведомления значение ни на что не влияет.*  <br> **ItemType**: *Тип элемента списка.*  <br> **ItemId**: *Id элемента списка.*  <br> **StepNumber**: *Id шага процесса уведомления.*  <br> **AddIfCreated**: *Укажите, надо ли добавлять уведомление, если уже добавлено уведомление с такими же ItemType, ItemId, StepNumber и NotificationSetting. Значение по умолчанию: false.*  |
| DefaultParseTemplate(String Template) | Парсинг шаблона по тегам Filled, Field, FormUrl, History.  <br> **Template**: *Шаблон для парсинга.*  |
| EndReminders(String ItemType) | Завершение Reminder'ов, отфильтрованных по ItemType.  <br> **ItemType**: *Тип элемента списка.*  |
| EndReminders(String ItemType, String ItemId) | Завершение Reminder'ов, отфильтрованных по ItemType, ItemId.  <br> **ItemType**: *Тип элемента списка.*  <br> **ItemId**: *Id элемента списка.*  |
| EndReminders(String ItemType, String ItemId, String StepNumber) | Завершение Reminder'ов, отфильтрованных по ItemType, ItemId, StepNumber.  <br> **ItemType**: *Тип элемента списка.*  <br> **ItemId**: *Id элемента списка.*  <br> **StepNumber**: *Id шага процесса уведомления.*  |
| GetNotificationUsers(SPFieldLookupValueCollection LookupValues) | Получение пользователей для уведомления через lookupValues из NotificationUserList.  <br> **LookupValues**: *Lookup'ы к списку NotificationUserList.*  |
| UpdateReminders(DateTime CheckDate) | Обновление всех Reminder'ов по условию (End = 0 AND NotificationDate <= CheckDate).             Если Reminder (элемент списка ReminderNotificationList) подходит под эти условия,             то создается элемент в NotificationList и к Reminder.NotificationDate добавляется ReminderSendPeriod из списка NotificationSettings.  <br> **CheckDate**: *Дата, с которой необходимо сравнить NotificationDate.*  |

#### Samples
```csharp

public void CreateNotificationByProcessStep()
{
    // узел со списками настроек уведомлений
    SPWeb web = Settings.Mock.Web;
    
    // список настроек шагов процесса
    SPList processList = Settings.Mock.Lists["ProcessStepList"];

    // шаг процесса
    SPListItem processStep = processList.GetItemById(1);

    // Данные, по которым формируется уведомление.
    List<DataItem> dataItems = GetDataItems();

    Notifications notifications = new Notifications(web, dataItems);

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
}
```
```csharp

public void CreateNotificationBySetting()
{
    SPWeb web = Settings.Mock.Web;
    
    // Данные, по которым формируется уведомление.
    List<DataItem> dataItems = GetDataItems();

    Notifications notifications = new Notifications(web, dataItems);

    // получение настройки уведомления
    NotificationSetting setting = new NotificationSetting(notifications.NotificationSettingsList);
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
}
```
```csharp

public void CreateNotificationBySettingTitle()
{
    SPWeb web = Settings.Mock.Web;

    // Данные, по которым формируется уведомление.
    List<DataItem> dataItems = GetDataItems();

    Notifications notifications = new Notifications(web, dataItems);

    // Формирование уведомления и добавление  в NotificationList 
    // или в ReminderNotificationList
    bool created = notifications.CreateByTitle(
        // Название элемента в списке NotificationSettings
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
}
```
