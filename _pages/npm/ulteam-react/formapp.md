---
title: ulteam-react FormApp
permalink: /npm/ulteam-react/formapp/
---

## FormApp component

Generate your form with controls from [office-ui-fabric-react](https://www.npmjs.com/package/office-ui-fabric-react) package.
Configure form fields and component aggregates all field values in one plain object.

### Demo
Try component on the [demo](/npm/ulteam-react/demo/?r=basicform)

### Sample

```tsx
import { PrimaryButton } from 'office-ui-fabric-react/lib/components/Button/PrimaryButton/PrimaryButton';
import { IPersonaProps } from 'office-ui-fabric-react/lib/components/Persona/Persona.types';
import { ITag } from 'office-ui-fabric-react/lib/components/pickers/TagPicker/TagPicker.types';
import * as React from 'react';
import { FormApp, FormFields, IErrorField, IFormConfig, IFormField } from '../../../..';
import { INumberFieldProps } from '../../../../form/data/FieldTypes';
import { IFormFieldDisabled, IFormFieldHidden } from '../../../../form/data/Interfaces';
import { ITestFormPageState } from './ITestFormPageState';
import { Toggle } from 'office-ui-fabric-react/lib/components/Toggle/Toggle';
import { Icon } from 'office-ui-fabric-react/lib/components/Icon/Icon';

export interface ISampleFields {
  title?: string;
  numberField?: number;
  doubleNumberField?: number;
  datePickerField?: Date;
  booleanField: boolean;
  name?: string;
  choiceField?: number;
  peoplePickerField?: IPersonaProps[];
  pickerField?: ITag[];
  conditionTextField?: string;
}

export class TestFormPage extends React.Component<{}, ITestFormPageState> {
  private currentFormFields: any = {};
  constructor(props: {}, state: ITestFormPageState) {
    super(props); 

    this.currentFormFields = this.getDefaultFormFields();

    this.state = {
      addCustomLabel: false,
      disablePicker: true,
      formFields: this.getDefaultFormFields()
    };
  }

  public shouldComponentUpdate(nextProps: {}, nextState: ITestFormPageState) {
    return nextState.addCustomLabel !== this.state.addCustomLabel ||
      nextState.disablePicker !== this.state.disablePicker ||
      nextState.formFields !== this.state.formFields;
  }

  public render() {
    console.log('state', this.state);

    return (
      <div className="form">
        <PrimaryButton 
          text="Clear field values"
          onClick={this.handleClearFieldClick} 
        />
        <div>
          <h1>Labels on the top</h1>
          <FormApp key={1}
                  config={this.getFormConfig()}
                  customClass="custom-class"
                  fieldValues={this.state.formFields}
                  handleFieldValues={this.handleChangeFieldValues}
                  checkRequired={false} />

        </div>
        <p></p>
        <Toggle label="Add custom label html to 'Title' field" onText="On" offText="Off" 
          onChange={this.handleAddCustomTable}
          defaultChecked={this.state.addCustomLabel}
        />
        <div>
          <h1>Labels on the left</h1>
          <FormApp key={2}
                  config={this.getFormConfig(this.state.addCustomLabel)}
                  fieldValues={this.state.formFields}
                  handleFieldValues={this.handleChangeFieldValues}
                  labelsOnTheLeft={true}
                  checkRequired={false} />

        </div>
        <p></p>
        <div>
          <h1>Required fieds</h1>
          <FormApp key={3}
                  config={this.getFormConfig()}
                  fieldValues={this.state.formFields}
                  handleFieldValues={this.handleChangeFieldValues}
                  checkRequired={true} />

        </div>
        
      </div>
    );
  }

  private addLabelHtml = (config: IFormField<any>, fieldValue?: any, formId?: number | undefined): JSX.Element | undefined => {
    return (
      <Icon iconName="Info" title="Custom label html" style={ {fontSize: 16} } />
    )
  }

  private getDefaultFormFields(): ISampleFields {
    return {
      booleanField: false,
      choiceField: 10,
      doubleNumberField: 2,
      datePickerField: new Date(2000, 1, 1),
      conditionTextField: '',
      name: 'test name',
      numberField: 1,
      peoplePickerField: [{
        id: '1',
        text: 'User name 1',
        secondaryText: 'Job title 1'
      }],
      pickerField: [{
        key: 'Key 2',
        name: 'Value 2'
      }],
      title: 'test title'
    };
  }

  public async getPeopleList(): Promise<IPersonaProps[]> {
    const result: IPersonaProps[] = [];

    await this.delay(1000);

    for (let i = 0; i < 20; i++) {
      const item: IPersonaProps = {
        id: i.toString(),
        text: `User name ${i}`,
        secondaryText: `Job title ${i}`
      };
      result.push(item);
    }

    return result;
  }

  public onChangeNumberField = (
    config: IFormField<INumberFieldProps>, 
    newValue: any, 
    prevValue: any, 
    prevFormFieldValues: ISampleFields
    ): ISampleFields => {
      
    let result: ISampleFields = prevFormFieldValues;

    result.numberField = newValue;
    if (!isNaN(newValue)) {
      result.doubleNumberField = newValue * 2;
    }

    return result;
  }

  public disabledPickerField = (
    config: IFormField<any>, 
    newValue: boolean, 
    prevValue: boolean, 
    newFormFieldValues: ISampleFields, 
    disabledMap: IFormFieldDisabled[]): IFormFieldDisabled[] => {

      disabledMap
      .filter(x => x.name == 'pickerField')[0]
      .disabled = !newValue;

    return disabledMap;
  }

  public hideConditionTextField = (
    config: IFormField<any>, 
    newValue: boolean, 
    prevValue: boolean, 
    newFormFieldValues: ISampleFields, 
    hiddenMap: IFormFieldHidden[]): IFormFieldHidden[] => {

    hiddenMap
      .filter(x => x.name == 'conditionTextField')[0]
      .hidden = !newValue;

    return hiddenMap;
  }

  public numberValidation = (config: IFormField<any>, newValue: any): string | undefined => {
    return isNaN(newValue) ? 
      'Value should be a number.' : 
      undefined;
  }

  public numberFieldError = (config: IFormField<any>, newValue: any, newFormFieldValues: any, errorField: IErrorField): IErrorField => {
    if (newFormFieldValues && newFormFieldValues.booleanField === true && newValue === '') {
      errorField.isError = true;
      errorField.message = "Hey!! I'm empty!!"
    }

    return errorField;
  }

  public getFormConfig(addCustomLabel?: boolean): IFormConfig {
    return {
      groups: [{
        expand: true,
        hideHeader: true,
        title: 'Common',
        fields: [
          FormFields.TextField('title', {
            label: 'Title',
            onRenderLabel: addCustomLabel === true ? this.addLabelHtml : undefined,
            labelsOnTheLeftClassName: 'labelsOnTheLeft-class',
            customClass: 'customClass-class'
          },
          {
            required: true,
            description: 'field description',
            errorMessage: 'Required field!!!',
            // value: defaultValues.title
          }),
          FormFields.NumberField('numberField', {
            label: 'Source number',
            // hidden: this.currentFormFields.title !== 'test',
            errorOnChange: this.numberFieldError,
            onChange: this.onChangeNumberField,
            validationErrorOnChange: this.numberValidation
          },
          {
            useCommaDelimiter: true,
            autoValidation: true,
            round: 2
          }),
          FormFields.NumberField('doubleNumberField', {
            label: 'Double number',
            // disabled: true,
            // validationErrorOnChange: this.numberValidation
          },
          {
            autoValidation: true,
            round: 0
            // value: defaultValues.doubleNumberField
          }),
          FormFields.PeoplePickerField('peoplePickerField',
          {
            label: 'People picker'
          }, 
          {
            itemLimit: 1,
            onResolveSuggestions: this.peoplePickerOnResolve,
            resolveDelay: 300,
            required: true,
            errorMessage: 'Required field!!!',
            suggestionProps: {
              noResultsFoundText: 'No items',
              loadingText: 'Searching...',
              suggestionsHeaderText: 'Searching results'
            }
          }),
          FormFields.DatePickerField('datePickerField',
          {
            label: 'Date picker label'
          },
          {
            description: 'description',
            errorMessage: 'Required field!!!',
            placeholder: 'Placeholder text...',
            required: true,
            officeUIProps: {
              isMonthPickerVisible: false
            }
          }),
          FormFields.BooleanField('booleanField', {
            label: 'your confirmation',
            hideOnChange: this.hideConditionTextField,
            disabledOnChange: this.disabledPickerField
          }, 
          {
            // value: defaultValues.booleanField
          }),
          FormFields.TextField('conditionTextField', {
            label: 'Condition Text Field',
            hidden: true          
          },
          {
            // value: defaultValues.conditionTextField
          }),
          FormFields.PickerField('pickerField', {
            disabled: this.state.disablePicker,
            label: 'Picker field',
            customClass: 'customClass'
          },
          {
            itemLimit: 1,
            noResultsFoundText: 'No results',
            suggestionsHeaderText: 'Results',
            errorMessage: 'Required field!!!',
            placeholder: 'Type for start search',
            required: true,
            resolveDelay: 300,
            openItemsOnEmptyFocus: true,
            // value: [{
            //   key: 'Key 2',
            //   name: 'Value 2'
            // }],
            options: [
              {
                key: 'Key 1',
                name: 'Value 1'
              },
              {
                key: 'Key 2',
                name: 'Value 2'
              },
              {
                key: 'Key 3',
                name: 'Value 3'
              }
            ]
          }),
          FormFields.ChoiceField('choiceField', {
            label: 'Choice'
          },
          {
            // value: defaultValues.choiceField,
            required: true,
            errorMessage: 'Required field!!!',
            placeholder: 'Select a value',
            options: [
              {
                key: 1,
                text: 'Text 1'
              },
              {
                key: 10,
                text: 'Text 10'
              },
              {
                key: 3,
                text: 'Text 3'
              }
            ]
          }),
          FormFields.ChoiceField('multiChoiceField', {
            label: 'Multi Choice'
          },
          {
            placeholder: 'Select a value',
            multiSelect: true,
            options: [
              {
                key: 1,
                selected: true,
                text: 'Text 1'
              },
              {
                key: 10,
                text: 'Text 10'
              },
              {
                key: 3,
                text: 'Text 3'
              }
            ]
          })
        ]
      },
      {
        title: 'Others',
        fields: [
          FormFields.TextField('name', {
            label: 'Name'
          },
          {
            // value: defaultValues.name,
            multiline: true,
            multilineAutoHeight: true,
            multilineResizable: true,
            multilineRows: 3,
            errorMessage: 'Required field!!!',
            required: true
          })
        ]
      }
    ]};
  }

  private handleAddCustomTable = (event: React.MouseEvent<HTMLElement, MouseEvent>, checked?: boolean | undefined) => {
    this.setState({ addCustomLabel: checked });
  }

  private handleChangeFieldValues = (formFields: any, errorFields: IErrorField[]) => {
    // const fields: ISampleFields = formFields as ISampleFields;
    
    this.currentFormFields = formFields;

    
    this.setState({ 
      formFields
    });

    console.log(this.currentFormFields);
    console.log('errorFields', errorFields);
  }

  private handleClearFieldClick = () => {
    const emptyValues: ISampleFields = {
      booleanField: false
    }
    this.setState({ formFields: emptyValues });
  }

  private peoplePickerOnResolve = (
    filterText: string,
    currentPersonas: IPersonaProps[],
    limitResults?: number
  ): IPersonaProps[] | Promise<IPersonaProps[]> => {
    if (filterText.length > 2) {
      return this.getPeopleList();
    }
    else {
      return [];
    }
  }

  public async delay(ms: number) {
    return new Promise( resolve => setTimeout(resolve, ms) );
  }
}
```


### IFormAppProps

| Property Name | Required | Type | Comments |
|-|-|-|-|
 | asTableRow | `Optional` |  *boolean* |     Table row form view       |  
 | checkRequired |  |  *boolean* |     Add error message if required value is empty       |  
 | config |  |  *IFormConfig* |     Form field configuration       |  
 | currentFieldId | `Optional` |  *string* |     Current editing field. Used for UlTable optimization       |  
 | customClass | `Optional` |  *string* |     Add custom class to main div       |  
 | errorType | `Optional` |  *FormFieldErrorType* |     Field error type       |  
 | fieldNavByArrows | `Optional` |  *boolean* |     Add field navigation by keyboard arrows and enter buttons. Using in UlTable component       |  
 | fieldValues | `Optional` |  *any* |     Form fields as key value pairs. If value is undefined then form render with values from form field configuration (IFormAppProps.config)       |  
 | formId | `Optional` |  *number* |     Form id. Its value will be return in handleFieldValues function       |  
 | handleFieldNav | `Optional` |  *function* |     Fires if in control press arrow or enter buttons       |  
 | handleFieldOnClick | `Optional` |  *function* |     Fires if user clicked on any field control       |  
 | handleFieldValues |  |  *function* |     Fires if any field value has changed       |  
 | handleOnSelection | `Optional` |  *function* |     WARNING: It's prop using in UlTable. Handle on selection row in UlTable       |  
 | isFixed | `Optional` |  *boolean* |     Indicate than form is fixed column in UlTable       |  
 | isSelected | `Optional` |  *boolean* |     WARNING: it's prop using only in UlTable component. Whether form row is selected or not.       |  
 | isSelectionMode | `Optional` |  *boolean* |     WARNING: it's prop using only in UlTable component. Set selection mode: single or multiple       |  
 | isShimmer | `Optional` |  *boolean* |     Show Office UI Shimmer component instead of field       |  
 | labelsOnTheLeft | `Optional` |  *boolean* |     If true then control label will be moved from the top of the control to the left.       |  
 | onComponentMount | `Optional` |  *function* |     Get form metadata with error fields after mount Use this if you need to know info about error fields directly after mount component       |  
 | readView | `Optional` |  *boolean* |     Form on read mode       |
