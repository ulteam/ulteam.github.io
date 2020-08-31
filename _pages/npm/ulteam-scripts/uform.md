---
title: ulteam-scripts UForm
permalink: /npm/ulteam-scripts/uform/
---

## UForm class

Helper methods for working with standard SharePoint list forms.
For correct working you shoud override standard CSR template using UOverride.init method.

### Sample

```tsx
import { Delay } from "../../common/Delay";
import { IUChoiceField, UForm, UOverride } from "../../sp";

export class TestJSLink {
  public static async run() {
    const override: UOverride = new UOverride({
      addLoading: true,
      hideInDispForm: ['Title'],
      hideInEditForm: ['Title'],
      hideInNewForm: ['Title'],
      Templates: { Fields: {
        'Title': {
          'NewForm': UOverride.setTextField,
          'EditForm': UOverride.setTextField
        },
      }}
    });

    override.init();

    // wait 2 seconds (just for test loading circle)
    await Delay.go(2000);
    // --- your async 'onload' code (for example, REST API calls)
    
    // unblock form controls
    UForm.setFormDisabled(false);
    
    const choices: IUChoiceField[] = [
      {
        value: 'Choice #1'
      },
      {
        value: 'Choice #2'
      },
      {
        value: 'Choice #3'
      }
    ];
    // set text field as multi choice
    UForm.setTextFieldAsMultiChoice('TextField', false, ',', choices, 'Choice #1', (key: string, newValue: string, container: HTMLDivElement) => {
      console.log(key, newValue, container);
    });
    
    // disable one choice
    await Delay.go(2000);
    choices[0].disabled = true;
    UForm.setTextFieldAsMultiChoice('TextField', false, ',', choices, 'Choice #2', (key: string, newValue: string, container: HTMLDivElement) => {
      console.log(key, newValue, container);
    });

    // check in browser console what generated in UForm.formData object
    // this object generated in UOverride.init method
    console.log(UForm.formData);
  }
}
```


#### Properties

| Name | Static | Description |
|-|-|-|
| formData: IUFormData |  `Static`  | Current item field values & field schema. <br>For initialization this property you shoud override standard CSR template using UOverride.init method. |
| formType: UFormType |  `Static`  | Opened form type. |

#### Methods

| Name | Returns | Static | Description |
|-|-|-|-|
| addFieldListener(key: string, callback: undefined &#124; (key: string, newValue: string &#124; ISPClientPeoplePickerEntity[]) => void) | void |  `Static`  | Add field control listener for 'change' event.  <br> **key**: *Field internal name*  <br> **callback**: *Callback function for custom action after field control value was changed <br>*  |
| closestElement(element: HTMLElement, tagName: string) | HTMLElement &#124; null |  `Static`  | Get closest parent element.  <br> **element**: *Child element*  <br> **tagName**: *Closest parent tag name <br>*  |
| getAuthorId() | number |  `Static`  | Get form Author Id.  |
| getCustomControlId(key: string) | string &#124; undefined |  `Static`  | Get custom control id by customRenderType prop in fieldSchema.  <br> **key**: *Field internal name <br>*  |
| getEditorId() | number |  `Static`  | Get form Editor Id.  |
| getFieldControl(key: string) | HTMLElement &#124; null |  `Static`  | Get field control in Edit/New form.  <br> **key**: *Field internal name <br>*  |
| getFieldControlId(key: string) | string &#124; undefined |  `Static`  | Get field control id in Edit/New form.  <br> **key**: *Field internal name <br>*  |
| getFieldControlIdBySchema(schema: FieldSchema_InForm) | string &#124; undefined |  `Static`  | Get field control id in Edit/New form.  <br> **schema**: *Field schema <br>*  |
| getFieldRowElement(key: string) | HTMLElement &#124; null |  `Static`  | Get form field row (tr tag in form table)  <br> **key**: *Field internal name <br>*  |
| getFieldSchema(key: string) | IUFieldSchema &#124; undefined |  `Static`  | Get field schema  <br> **key**: *Field internal name <br>*  |
| getFormType() | UFormType |  `Static`  | Get SharePoint list form type by location.pathname.  |
| getItemValue(key: string) | string |  `Static`  | Get field value in SharePoint form and update this.item object  <br> **key**: *Field internal name <br>*  |
| getUserFieldValueId(key: string) | number &#124; undefined |  `Static`  | Get user field (not multiple) value id.  <br> **key**: *Field internal name <br>*  |
| hideFieldRow(key: string, hide: boolean) | void |  `Static`  | Set field row hidden.  <br> **key**: *Field internal name*  <br> **hide**: *Whether hide field row or not <br>*  |
| hideTimeInDatePicker(key: string, hide: boolean) | void |  `Static`  | Hide/show time in SharePoint date picker control.  <br> **key**: *Field internal name*  <br> **hide**: *Whether hide time or not <br>*  |
| setErrorMessage(key: string, message: string, show: boolean) | void |  `Static`  | Set error message below field control (like standard SharePoint field value error)  <br> **key**: *Field internal name*  <br> **message**: *Error message*  <br> **show**: *Whether show message or not <br>*  |
| setFieldSchemaType(key: string, type: UFieldRenderType) | void |  `Static`  | Set customRenderType prop in this.item.fieldSchema array  <br> **key**: *Field internal name*  <br> **type**: *Custom render type <br>*  |
| setFormDisabled(isDisabled: boolean) | void |  `Static`  | Disable/enable all form controls and buttons  <br> **isDisabled**: *Whether disable form or not <br>*  |
| setItemValue(key: string, value: any) | void |  `Static`  | Set new field value (include custom controls) in SharePoint form and update this.item object  <br> **key**: *Field internal name*  <br> **value**: *New field value <br>*  |
| setRequiredStar(key: string, addStar: boolean, starTitle: string) | void |  `Static`  | Add or delete required star to field label  <br> **key**: *Field internal name*  <br> **addStar**: *Whether add star or not*  <br> **starTitle**: *Star element title attribute <br>*  |
| setSaveBtn(preSaveAction: () => boolean) | void |  `Static`  | Add custom action on the save button.  <br> **preSaveAction**: *If function returns true then run standard SharePoint functionality on the save button. <br>*  |
| setTextFieldAsDisplayText(key: string, defaultValue: undefined &#124; string) | void |  `Static`  | Set text field as text in display form.  <br> **key**: *Field internal name*  <br> **defaultValue**: *Set default value. If value is undefined then value will not changed <br>*  |
| setTextFieldAsDropdown(key: string, disabled: boolean, loading: undefined &#124; false &#124; true, options: IULookupField[], defaultValue: undefined &#124; string) | void |  `Static`  | Set text field as dropdown.  <br> **key**: *Field internal name*  <br> **disabled**: *Whether control disabled or not*  <br> **loading**: **  <br> **options**: *Dropdown options*  <br> **defaultValue**: *Set default option for dropdown <br>*  |
| setTextFieldAsMultiChoice(key: string, loading: undefined &#124; false &#124; true, separator: string, choices: IUChoiceField[], defaultValue: undefined &#124; string, callback: undefined &#124; (key: string, newValue: string, container: HTMLDivElement) => void) | void |  `Static`  | Set SharePoint text field as multi choice (checkboxes)  <br> **key**: *Field internal name*  <br> **loading**: *Whether show loading circle or not*  <br> **separator**: *Value separator for SharePoint text field value*  <br> **choices**: *Array of all choices*  <br> **defaultValue**: *Default selected choices. For select several choices, use 'separator'*  <br> **callback**: *Add your action after 'change' event <br>*  |
| setTextFieldAsTable(key: string, columnsSchema: IUFieldTableColumnSchema[], isEdit: undefined &#124; false &#124; true, columnSeparator: undefined &#124; string, rowSeparator: undefined &#124; string, tableConsts: IUFieldTableConsts) | void |  `Static`  | Set text field as table.  <br> **key**: *Field internal name*  <br> **columnsSchema**: *Table columns*  <br> **isEdit**: *Whether table on edit mode or not*  <br> **columnSeparator**: *Column separator in SP field*  <br> **rowSeparator**: *Row separator in SP field*  <br> **tableConsts**: *Table consts <br>*  |
| unmountCustomControl(key: string, resetValue: boolean) | void |  `Static`  | Delete custom control and show standard control.  <br> **key**: *Field internal name*  <br> **resetValue**: *Whether clear current field value or not <br>*  |
