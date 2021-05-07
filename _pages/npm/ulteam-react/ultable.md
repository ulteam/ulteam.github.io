---
title: ulteam-react UlTable
permalink: /npm/ulteam-react/ultable/
---

## UlTable component

Generate your table with controls from [office-ui-fabric-react](https://www.npmjs.com/package/office-ui-fabric-react) package.
Configure table fields and component aggregates all rows values in one plain object.
Table has edit mode, shimmer mode. You can fix header or/and fix left columns.

### Demo
Try component on the [demo](/npm/ulteam-react/demo/?r=basictable)

### Sample

```tsx
import { Icon } from 'office-ui-fabric-react/lib/components/Icon/Icon';
import * as React from 'react';
import { FormFields, INumberFieldProps, IUlTableRow } from '../../../..';
import { UlTable } from '../../../../form/components/UlTable/UlTable';
import { IFormField } from '../../../../form/data/Interfaces';
import { ITestTablePageState } from './ITestTablePageState';
import { UlTableSelectionMode } from '../../../../form/components/UlTable/UlTable.types';
import { Dropdown } from 'office-ui-fabric-react/lib/components/Dropdown/Dropdown';
import { IDropdownOption } from 'office-ui-fabric-react/lib/components/Dropdown/Dropdown.types';

export interface ITestTableRowFields {
  column1: string;
  column2: number;
  column3: number;
  column4: number;
  column5: string;
}

const defaultValues: ITestTableRowFields = {
  column1: 'default value',
  column2: 0,
  column3: 0,
  column4: 0,
  column5: ''
};

/**
 * Test table view
 */
export class TestTablePage extends React.Component<{}, ITestTablePageState> {
  private tableKey: number = 0;
  private testValue: string = 'Hello!';
  constructor(props: {}, state: ITestTablePageState) {
    super(props); 
    this.state = {
      selectionMode: UlTableSelectionMode.Multiple,
      tableRows: this.getDefaultTableRows()
    };
  }
  
  public shouldComponentUpdate(nextProps: {}, nextState: ITestTablePageState): boolean {
    return this.state.tableRows !== nextState.tableRows ||
      this.state.selectionMode !== nextState.selectionMode;
  }

  public render() {
    const selectionModeOptions: IDropdownOption[] = [
      {
        key: 'None',
        text: 'None'
      },
      {
        key: UlTableSelectionMode.Single,
        text: UlTableSelectionMode.Single
      },
      {
        key: UlTableSelectionMode.Multiple,
        text: UlTableSelectionMode.Multiple
      }
    ];

    return (
      <div>
        <Dropdown 
          label="Table selection mode"
          options={selectionModeOptions} 
          onChange={this.handleSelectionModeChange}
          defaultValue="None"
          style={ { width: 200 } }
        />
        <div className="form">
          <UlTable 
            key={this.tableKey}
            checkRequired={true}
            customClass="customTableClass"
            handleCellClick={this.handleCellClick}
            handleChangeValues={this.handleChangeFieldValues}
            handleRowClass={this.handleRowClass}
            onComponentMount={this.onComponentMount}
            onChangeSelection={this.onChangeSelection}
            readViewNoFocus={true}
            fields={this.getFormConfig(defaultValues)}
            rowCustomClass="customRowClass"
            rows={this.state.tableRows}
            selectionMode={this.state.selectionMode}
          />
        </div>
      </div>
    );
  }

  private getDefaultTableRows(): IUlTableRow<ITestTableRowFields>[] {
    let result: IUlTableRow<ITestTableRowFields>[] = [];

    for (let i = 0; i < 100; i++) {
      result.push({
        fieldValues: {
          column1: defaultValues.column1 + (i + 1).toString(),
          column2: defaultValues.column2 + Math.ceil(i + 1 / 10),
          column3: defaultValues.column3,
          column4: defaultValues.column4,
          column5: defaultValues.column5,
        },
        id: i,
        isReadView: i == 1 ? true : undefined
      });
    }

    return result;
  }

  public numberValidation = (config: IFormField<any>, newValue: any): string | undefined => {
    return isNaN(newValue) ? 
      'Value should be a number.' : 
      undefined;
  }

  public handleFormulaOnChangeColumn2 = (
    config: IFormField<INumberFieldProps>, 
    newValue: any, 
    prevValue: any, 
    prevFormFieldValues: ITestTableRowFields
    ): ITestTableRowFields => {
    
    let result: ITestTableRowFields = prevFormFieldValues;

    result.column2 = newValue;
    if (!isNaN(newValue)) {
      result.column3 = newValue * 2;
    }

    return result;
  }

  public handleSelectionModeChange = (
    event: React.FormEvent<HTMLDivElement>, 
    option?: IDropdownOption | undefined) => {

    const selectionMode = option && option.key !== 'None' ?
      option.key as UlTableSelectionMode :
      undefined;

    this.tableKey++;
    this.setState({ selectionMode });
  }

  public column3InnerHtml = (config: IFormField<any>, fieldValue?: any, formId?: number): JSX.Element => {
    let result: JSX.Element = <div></div>;

    if (formId && formId < 20) {
      result = (
        <div className="table-cell-comments">
          <Icon iconName="CaretTopRightSolid8"  
            onClick={() => {
              alert(formId);
              console.log(this.testValue);
            }} />
        </div>
      );
    }

    return result;
  }

  private getFormConfig(rowFields: ITestTableRowFields): IFormField<any>[] {
    return [
      FormFields.TextField('column1', {
        label: 'Column 1',
        customClass: 'class-column1',
        headerFieldProps: {
          isFiltering: true
        }
      }, {
        required: true,
        errorMessage: 'Error!!!'
      }),
      FormFields.NumberField('column2', {
        label: 'Column 2',
        customClass: 'class-column2',
        onChange: this.handleFormulaOnChangeColumn2,
        headerFieldProps: {
          customActions: [{
            key: 'CustomAction',
            text: 'Custom action',
            onClick: () => { alert(this.testValue )}
          }],
          isFiltering: true,
          isSorting: true
        },
        validationErrorOnChange: this.numberValidation
      }),
      FormFields.TextField('column3', {
        label: 'Formula',
        customClass: 'class-column3',
        maxWidth: 70,
        minWidth: 70,
        flexGrow: 0.5,
        innerHtml: this.column3InnerHtml
      }),
      FormFields.NumberField('column4', {
        label: 'Column 4',
        customClass: 'class-column4'
      }),
      FormFields.TextField('column5', {
        label: 'Column 5',
        customClass: 'customMultiline'
      }, {
        multiline: true,
        multilineAutoHeight: true,
        multilineResizable: true,
        multilineRows: 1
      })
    ];
  }

  private handleCellClick = (fieldId: string, fieldConfig: IFormField<any>, formId?: number, fieldValue?: any) => {
    console.log('handleCellClick', fieldConfig, fieldValue);
  }

  private handleChangeFieldValues = (rows: IUlTableRow<ITestTableRowFields>[]) => {
    console.log(rows);
  }

  private handleRowClass = (fieldValues: any, rowId: number, rowIndex: number, isTotalRow?: boolean | undefined): string => {
    return rowIndex % 2 === 0 ? 'handleRowClass' : '';
  } 

  private onComponentMount = (rows: IUlTableRow<ITestTableRowFields>[]) => {
    console.log('onComponentMount', rows);
  }

  private onChangeSelection = (selectedRows: number[]) => {
    console.log('selectedRows', selectedRows);
  }
}
```


### IUlTableProps

| Property Name | Required | Type | Comments |
|-|-|-|-|
 | addTotalRow | `Optional` |  *boolean* |     Add total row on the bottom of the table. For handling add 'handleTotalRow' prop. WARN: it is working only for text and number field types       |  
 | checkRequired |  |  *boolean* |     Add error message if required value is empty       |  
 | customClass | `Optional` |  *string* |     Add custom class to main div       |  
 | defaultRowFieldName | `Optional` |  *string* |     Focus on the field by default       |  
 | defaultRowId | `Optional` |  *number* |     Focus on the row by default       |  
 | errorsAsTooltip | `Optional` |  *boolean* |     Error as Office UI Fabric Tooltip component       |  
 | fieldNavByArrows | `Optional` |  *boolean* |     Add cell navigation by keyboard arrows and enter buttons       |  
 | fields |  |  *Array‹[IFormField](interfaces/iformfield.md)‹any››* |     Row fields configuration       |  
 | fixHeight | `Optional` |  *number* |     Table row       |  
 | handleCellClick | `Optional` |  *function* |     Click event on any cell in table       |  
 | handleChangeValues |  |  *function* |     Fires if any field (cell) value has changed       |  
 | handleRowClass | `Optional` |  *function* |     Add your class to row related on row data       |  
 | handleTotalRow | `Optional` |  *function* |     If you want to add total row in table, you should set property addTotalRow = true Set values for total row. WARN: it is working only for text and number field types       |  
 | hideHeader | `Optional` |  *boolean* |     Hide table header or not       |  
 | isShimmer | `Optional` |  *boolean* |     Show Office UI Shimmer component instead of field       |  
 | onChangeSelection | `Optional` |  *function* |  |  
 | onComponentMount | `Optional` |  *function* |     Get table metadata with error fields after mount Use this if you need to know info about error fields directly after mount component       |  
 | readView | `Optional` |  *boolean* |     Table on read mode       |  
 | readViewNoFocus | `Optional` |  *boolean* |     No focused rows will always be on read mode       |  
 | rowCustomClass | `Optional` |  *string* |     Add custom class to row div       |  
 | rows |  |  *Array‹[IUlTableRow](interfaces/iultablerow.md)‹any››* |     Table row values and errors       |  
 | scrollOptions | `Optional` |  *IUlTableScrollOptions* |     Add scroll to the table and fix header on the top       |  
 | selectionMode | `Optional` |  *UlTableSelectionMode* |     Controls how/if the details list manages selection. Options include single, multiple       |  
 | shimmerRowCount | `Optional` |  *number* |  |
